
## Supplier entity creatoon and get :

# Get


``` abap
CLASS zcl_ztest_am_at_sample_dpc_ext DEFINITION
  PUBLIC
  INHERITING FROM zcl_ztest_am_at_sample_dpc
  CREATE PUBLIC .

  PUBLIC SECTION.

  PROTECTED SECTION.
    METHODS productset_get_entityset  REDEFINITION.
    METHODS productset_get_entity     REDEFINITION.
    METHODS productset_create_entity  REDEFINITION.
    METHODS productset_update_entity  REDEFINITION.
    METHODS productset_delete_entity  REDEFINITION.

    METHODS supplierset_get_entityset REDEFINITION.
    METHODS supplierset_get_entity    REDEFINITION.
    METHODS supplierset_create_entity REDEFINITION.
    METHODS supplierset_update_entity REDEFINITION.
    METHODS supplierset_delete_entity REDEFINITION.

  PRIVATE SECTION.
ENDCLASS.



CLASS zcl_ztest_am_at_sample_dpc_ext IMPLEMENTATION.
  METHOD productset_get_entityset.

    " STEP 1 DATA DECLARATION
    DATA : lv_top        TYPE i,
           lv_skip       TYPE i,
           lv_total      TYPE i,
           ls_row        TYPE bapi_epm_max_rows,
           ls_cat_filter TYPE bapi_epm_product_categ_range,
           " TODO: variable is assigned but only used in commented-out code (ABAP cleaner)
           lt_cat_filter TYPE STANDARD TABLE OF bapi_epm_product_categ_range,
           lt_data       TYPE TABLE OF bapi_epm_product_header.

*           ls_entity TYPE zcl_ztest_am_at_sample_mpc=>ts_product.

    lv_top = is_paging-top.
    lv_skip = is_paging-skip.
    lv_total = lv_top + lv_skip.

    ls_row-bapimaxrow = lv_total.

    READ TABLE it_filter_select_options  INTO FINAL(ls_filter) INDEX 1.


    LOOP AT ls_filter-select_options INTO FINAL(ls_filter_selop).
      MOVE-CORRESPONDING ls_filter_selop TO ls_cat_filter.
      APPEND ls_cat_filter TO lt_cat_filter.
    ENDLOOP.


*SETP 2 CALL BAPI AND GET THE DATA
    CALL FUNCTION 'BAPI_EPM_PRODUCT_GET_LIST'
      EXPORTING
        max_rows           = ls_row
      TABLES
        headerdata         = lt_data
*                   selparamproductid
*                   selparamsuppliernames
        selparamcategories = lt_cat_filter
*                   RETURN
      .
    et_entityset = VALUE #( FOR wa IN lt_data FROM lv_skip
                            ( CORRESPONDING #( wa ) ) ).

    REFRESH et_entityset.

    IF lv_total > 0.
*      LOOP AT lt_data INTO FINAL(ls_data) FROM lv_skip + 1.
**STEP 3  RETURN THE DATA OUT
*        ls_entity = CORRESPONDING #( ls_data ).
*        APPEND ls_entity TO et_entityset.
*      ENDLOOP.

      et_entityset = VALUE #( FOR wa IN lt_data FROM
                              ( lv_skip + 1 )
                              ( CORRESPONDING #( wa ) ) ).

    ELSE.

      et_entityset = CORRESPONDING #( lt_data ).

    ENDIF.

  ENDMETHOD.

  METHOD productset_get_entity.
    DATA : lv_prod_id TYPE bapi_epm_product_id,
           ls_header  TYPE bapi_epm_product_header,
           lt_ret     TYPE TABLE OF bapiret2.

    " STEP 1 Know the key passed by the user
    READ TABLE it_key_tab INTO FINAL(ls_key) INDEX 1.
    " step 2 Extract the product id from the key
    lv_prod_id = ls_key-value.
    " call the bapi wrt the product id
    IF lv_prod_id IS INITIAL.

      RAISE EXCEPTION NEW /iwbep/cx_mgw_busi_exception( " TODO: check spelling: doesnt (typo) -> doesn't (ABAP cleaner)
          message_unlimited = 'Product Id doesnt exists in the DB' ).
    ELSE.
      CALL FUNCTION 'BAPI_EPM_PRODUCT_GET_DETAIL'
        EXPORTING
          product_id = lv_prod_id
        IMPORTING
          headerdata = ls_header
        TABLES
          return     = lt_ret.

      DATA(lo_cont) =  me->mo_context->get_message_container( ).

      lo_cont->add_messages_from_bapi(
        it_bapi_messages          = lt_ret
*         iv_error_category         =
*         iv_determine_leading_msg  =
*         iv_entity_type            =
*         it_key_tab                =
*         iv_add_to_response_header = abap_false
      ).

      " map data to output structure of odata
      er_entity = CORRESPONDING #( ls_header ).
    ENDIF.

  ENDMETHOD.

  METHOD productset_create_entity.

    DATA : ls_entity TYPE zcl_ztest_am_at_sample_mpc=>ts_product,
           ls_header TYPE bapi_epm_product_header,
           lt_ret    TYPE STANDARD TABLE OF bapiret2.

    " STEP 1 : READ THE INCOMING DATA
    TRY.
        io_data_provider->read_entry_data( IMPORTING es_data = ls_entity ).
      CATCH /iwbep/cx_mgw_tech_exception.
    ENDTRY.

    MOVE-CORRESPONDING ls_entity TO ls_header.

    " STEP 2 : CALL BAPI TO INSERT DATA

    CALL FUNCTION 'BAPI_EPM_PRODUCT_CREATE'
      EXPORTING
        headerdata = ls_header
*       persist_to_db = abap_true
      TABLES
*       conversion_factors =
        return     = lt_ret.

    " STEP 3 : EXCEPTION HANDLING

    IF lt_ret IS NOT INITIAL.
      FINAL(lo_cont) = me->mo_context->get_message_container( ).

      lo_cont->add_messages_from_bapi( it_bapi_messages = lt_ret
*                                       iv_error_category =
*                                       iv_determine_leading_msg =
*                                       iv_entity_type   =
*                                       it_key_tab       =
*                                       iv_add_to_response_header = abap_false
      ).

      RAISE EXCEPTION NEW /iwbep/cx_mgw_busi_exception( message_container = me->mo_context->get_message_container( ) ).
    ENDIF.

    " STEP 4 : RETURN THE CREATED DATA OUT
    MOVE-CORRESPONDING ls_header TO er_entity.

  ENDMETHOD.

  METHOD productset_update_entity.

    DATA : ls_entity  TYPE zcl_ztest_am_at_sample_mpc=>ts_product,
           ls_header  TYPE bapi_epm_product_header,
           lv_prod_id TYPE bapi_epm_product_id,
           ls_headerx TYPE bapi_epm_product_headerx,
           lt_ret     TYPE STANDARD TABLE OF bapiret2.

    " STEP 1 : READ THE INCOMING DATA
    TRY.
        io_data_provider->read_entry_data( IMPORTING es_data = ls_entity ).
      CATCH /iwbep/cx_mgw_tech_exception.
    ENDTRY.

    MOVE-CORRESPONDING ls_entity TO ls_header.
    lv_prod_id = ls_header-product_id.

    ls_headerx-product_id    = lv_prod_id.
    ls_headerx-price         = abap_true.
    ls_headerx-currency_code = abap_true.
    ls_headerx-supplier_id   = abap_true.
    ls_headerx-name          = abap_true.
    ls_headerx-description   = abap_true.

    " STEP 2 : CALL BAPI TO INSERT DATA
    CALL FUNCTION 'BAPI_EPM_PRODUCT_CHANGE'
      EXPORTING
        product_id  = lv_prod_id
        headerdata  = ls_header
        headerdatax = ls_headerx
*       persist_to_db = abap_true
      TABLES
*       conversion_factors =
        return      = lt_ret.

    " STEP 3 : EXCEPTION HANDLING

    IF lt_ret IS NOT INITIAL.
      FINAL(lo_cont) = me->mo_context->get_message_container( ).

      lo_cont->add_messages_from_bapi( it_bapi_messages = lt_ret
*                                       iv_error_category =
*                                       iv_determine_leading_msg =
*                                       iv_entity_type   =
*                                       it_key_tab       =
*                                       iv_add_to_response_header = abap_false
      ).

      RAISE EXCEPTION NEW /iwbep/cx_mgw_busi_exception( message_container = me->mo_context->get_message_container( ) ).
    ENDIF.

    " STEP 4 : RETURN THE CREATED DATA OUT
    MOVE-CORRESPONDING ls_header TO er_entity.

  ENDMETHOD.

  METHOD productset_delete_entity.
    DATA lv_prod_id TYPE bapi_epm_product_id.
    DATA lt_ret     TYPE STANDARD TABLE OF bapiret2.

    FINAL(ls_key) = VALUE /iwbep/s_mgw_name_value_pair( it_key_tab[ 1 ] OPTIONAL  ).

    lv_prod_id = ls_key-value.

    CALL FUNCTION 'BAPI_EPM_PRODUCT_DELETE'
      EXPORTING
        product_id = lv_prod_id
*       persist_to_db = abap_true
      TABLES
        return     = lt_ret
                     EXCEPTIONS
                     cx_sy_dyn_call_illegal_type.

  ENDMETHOD.

  METHOD supplierset_create_entity.

  ENDMETHOD.

  METHOD supplierset_delete_entity.

  ENDMETHOD.

  METHOD supplierset_get_entity.

     DATA : lv_bp_id TYPE bapi_epm_BP_id,
           ls_header  TYPE bapi_epm_bp_header,
           lt_ret     TYPE TABLE OF bapiret2.

    " STEP 1 Know the key passed by the user
    READ TABLE it_key_tab INTO FINAL(ls_key) INDEX 1.
    " step 2 Extract the BP id from the key
    lv_bp_id = ls_key-value.
    " call the bapi wrt the BP id
    IF lv_bp_id IS INITIAL.

      RAISE EXCEPTION NEW /iwbep/cx_mgw_busi_exception( " TODO: check spelling: doesnt (typo) -> doesn't (ABAP cleaner)
          message_unlimited = 'BP Id doesnt exists in the DB' ).
    ELSE.
      CALL FUNCTION 'BAPI_EPM_BP_GET_DETAIL'
        EXPORTING
          BP_id = lv_bp_id
        IMPORTING
          headerdata = ls_header
        TABLES
          return     = lt_ret.

      DATA(lo_cont) =  me->mo_context->get_message_container( ).

      lo_cont->add_messages_from_bapi(
        it_bapi_messages          = lt_ret
*         iv_error_category         =
*         iv_determine_leading_msg  =
*         iv_entity_type            =
*         it_key_tab                =
*         iv_add_to_response_header = abap_false
      ).

      " map data to output structure of odata
      er_entity = CORRESPONDING #( ls_header ).
    ENDIF.

  ENDMETHOD.

  METHOD supplierset_get_entityset.

    " STEP 1 DATA DECLARATION
    DATA : lv_top   TYPE i,
           lv_skip  TYPE i,
           lv_total TYPE i,
           ls_row   TYPE bapi_epm_max_rows,
           lt_data  TYPE TABLE OF bapi_epm_bp_header.

*           ls_entity TYPE zcl_ztest_am_at_sample_mpc=>ts_bp.

    lv_top = is_paging-top.
    lv_skip = is_paging-skip.
    lv_total = lv_top + lv_skip.

    ls_row-bapimaxrow = lv_total.

*SETP 2 CALL BAPI AND GET THE DATA
    CALL FUNCTION 'BAPI_EPM_BP_GET_LIST'
      EXPORTING max_rows   = ls_row
      TABLES    bpheaderdata  = lt_data.
*                   RETURN
    et_entityset = VALUE #( FOR wa IN lt_data FROM lv_skip
                            ( CORRESPONDING #( wa ) ) ).

    REFRESH et_entityset.

    IF lv_total > 0.
*      LOOP AT lt_data INTO FINAL(ls_data) FROM lv_skip + 1.
**STEP 3  RETURN THE DATA OUT
*        ls_entity = CORRESPONDING #( ls_data ).
*        APPEND ls_entity TO et_entityset.
*      ENDLOOP.

      et_entityset = VALUE #( FOR wa IN lt_data FROM
                              ( lv_skip + 1 )
                              ( CORRESPONDING #( wa ) ) ).

    ELSE.

      et_entityset = CORRESPONDING #( lt_data ).

    ENDIF.

  ENDMETHOD.

  METHOD supplierset_update_entity.

  ENDMETHOD.

ENDCLASS.

```


## Multiple ( entity set)
<img width="1392" height="864" alt="image" src="https://github.com/user-attachments/assets/a137dbc6-221e-4764-a6c0-5dd55c34521e" />

## single entity 
<img width="1325" height="725" alt="image" src="https://github.com/user-attachments/assets/193d9fd6-17a6-4438-bd9b-1ea8866b687e" />



