# OData Post (create )

<img width="1504" height="864" alt="image" src="https://github.com/user-attachments/assets/08ee204d-8a69-4013-8d6a-5e93bd5ef4c6" />

<img width="1538" height="914" alt="image" src="https://github.com/user-attachments/assets/bbc90380-1ba1-4b9b-a66e-0d0108296f36" />

<img width="1428" height="865" alt="image" src="https://github.com/user-attachments/assets/91a72131-08cc-4272-ba7b-20b40fd95246" />

# Put ( update )( full chaqnge )

# patch ( update few fields only)

<img width="1505" height="865" alt="image" src="https://github.com/user-attachments/assets/74fc63ea-cdd0-404f-9ad5-f254f9a08136" />

<img width="1503" height="859" alt="image" src="https://github.com/user-attachments/assets/32dee7d7-8a46-4595-8c82-91a61a0e7a4f" />


# Delete

``` abap

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
      EXPORTING product_id    = lv_prod_id
*                persist_to_db = abap_true
      TABLES    return        = lt_ret
      EXCEPTIONS
      cx_sy_dyn_call_illegal_type.

  ENDMETHOD.
```

<img width="1348" height="900" alt="image" src="https://github.com/user-attachments/assets/b4bef288-60b3-46c0-9c2a-ee3cc9f6a5a7" />






