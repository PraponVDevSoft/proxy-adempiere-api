## Módulo Interfaz de Usuario

### POST /adempiere-api/ui/attachment

Obtener Adjunto

#### Paràmetros POST:

`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`id` - id de referencia.
`uuid` - uuid de referencia.
#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/attachment?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"table_name": "AD_Test","id": "50000","uuid": "a4cb498e-fb40-11e8-a479-7a0060f0aa01"}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result": {
        "attachmentUuid": "771d2187-6103-430a-acfc-aee208f22a0c",
        "title": "Attachment Title",
        "textMsg": "",
        "resourceReferencesList": [
            {
                "tableName": "AD_Test",
                "resourceUuid": "771d2187-6103-430a-acfc-aee208f22a0c"
            }
        ]
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/resource-reference

Información de referencia de recursos

#### Paràmetros POST:

`image_id` - id de la imagen
#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/resource-reference?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"imageId": 5475}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result": {
        "resourceUuid": "771d2187-6103-430a-acfc-aee208f22a0c",
        "fileName": "test.jpeg",
        "fileSize": 1.3,
        "description": "any imgage test",
        "textMsg": "",
        "contentType": "image/jpeg"
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/create-chat-entry

Crear una entrada de chat

#### Paràmetros POST:

`uuid` - uuid del registro.
`id` - id del registro.
`table_name` - nombre de la tabla (obligatorio para obtener la traducción).
`comment` - comentario

#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
	"language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/create-chat-entry?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"table_name": "C_Order","id": "1073741", "uuid": "6ff7ed30-4bb1-4eeb-9e84-b6fa01978d66", "comment": "add comment"}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result": {
        "chat_uuid": "e22d49ba-39c3-4edb-bd84-4bb7066429b8",
        "uuid": "2ac7eee1-dbe8-4834-beee-663dde88cd60",
        "id": 1000005,
        "subject": "",
        "character_data": "add comment",
        "user_uuid": "",
        "user_name": "",
        "chat_entry_type": 0,
        "chat_entry_type_name": 0,
        "confidential_type": 0,
        "confidential_type_name": 0,
        "moderator_status": 1,
        "moderator_status_bname": 1,
        "log_date": "2021-02-18T20:21:05.000Z"
    }
}
```

#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/get-report-output

Obtener la salida del informe

#### Paràmetros POST:

`printFormatUuid` - referencia de formato de impresión.
`reportViewUuid` - referencia de la vista del informe.
`isSummary` - resumen.
`reportName` - nombre del informe.
`reportType` - tipo de informe.
`columns` - columnas de la consulta.
`filters` - filtros de la consulta.
`tableName` - nombre de la tabla (obligatorio si no es una consulta).
`query` - consulta personalizada en lugar de un nombre de tabla basado en SQL.
`whereClause` - cláusula where de la búsqueda basada en SQL.
`orderByClause` - cláusula order by basada en SQL.
`limit` - límite de registros.

#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
	"language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/get-report-output?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"printFormatUuid": "771d2187-6103-430a-acfc-aee208f22a0c","reportViewUuid": "831d2187-1233-430a-acfc-aee208f64a0zv","isSummary": false,"reportName": "Report Name Test","reportType": "pdf","tableName": "AD_TEST","parametersList": []}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result":{
        "uuid": "771d2187-6103-430a-acfc-aee208f22a0c",
        "name": "Report Test",
        "description": "",
        "fileName": "",
        "output": [],
        "mimeType": "pdf",
        "dataCols": 7,
        "dataRows": 8,
        "headerName": "",
        "footerName": "",
        "printFormatUuid": "sd1d2199-6103-430a-acfc-aee208f22a0c",
        "reportViewUuid": "831d2187-1233-430a-acfc-aee208f64a0zv",
        "tableName": "",
        "outputStream": [],
        "reportType": "pdf"
    }

}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error


### POST /adempiere-api/ui/list-drill-tables

Obtener tablas para el taladro

#### Paràmetros POST:

`table_name` - nombre de la tabla (obligatorio si no es una consulta).

#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es",
    "pageSize": 50
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/list-drill-tables?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"tableName": "AD_TEST"}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code":200,
    "result":{
    "recordCount": 2,
    "drillTablesList": [{
        "tableName": "AD_TEST",
        "printName": "Test Name"
    },
        {
            "tableName": "AD_TEST",
            "printName": "Test Name 2"
        }
    ],
    "nextPageToken": "771d2187-6103-430a-acfc-aee208f22a0c-1"
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/list-report-views

Obtener tablas para la grilla

#### Paràmetros POST:

`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`processUuid` - uuid del proceso

#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es",
    "pageSize": 50
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/list-report-views?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"table_name":"RV_PrintFormatDetail","process_uuid":"a42a74fa-fb40-11e8-a479-7a0060f0aa01"}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result": {
        "record_count": 0,
        "next_page_token": "",
        "records": [
            {
                "report_view_uuid": "a4883f9a-fb40-11e8-a479-7a0060f0aa01",
                "name": "PrintFormat Detail",
                "description": "PrintFormat Detail",
                "table_name": "RV_PrintFormatDetail"
            }
        ]
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/list-print-formatss

Obtener formatos de impresión

#### Paràmetros POST:

`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`processUuid` - uuid del proceso.
`reportViewUuid` - uuid de la vista del informe.

#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es",
    "pageSize": 50
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/list-print-formatss?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{process_uuid: "a42a74fa-fb40-11e8-a479-7a0060f0aa01"}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result": {
        "record_count": 0,
        "next_page_token": "",
        "records": [
            {
                "print_format_uuid": "c35aefe8-1eec-46f9-b59c-d072f800e183",
                "name": "MIGO -> Imprimir Detalle de Formato",
                "description": "",
                "table_name": "RV_PrintFormatDetail",
                "is_default": false,
                "report_view_uuid": "a4883f9a-fb40-11e8-a479-7a0060f0aa01"
            }
        ]
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/unlock-private-access

Desbloquear un acceso privado

#### Paràmetros POST:

`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`id` - id del registro.
`uuid` - uuid del registro.

#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/unlock-private-access?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"table_name": "C_Order","id": "1073741","uuid": "6ff7ed30-4bb1-4eeb-9e84-b6fa01978d66"}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result": {
        "table_name": "C_Order",
        "id": 1073741,
        "uuid": "43adbe9d-04a7-4cf6-9582-895c1e40da0b"
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/lock-private-access

Bloquear un acceso privado

#### Paràmetros POST:

`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`id` - id del registro.
`uuid` - uuid del registro.

#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/lock-private-access?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"table_name": "C_Order","id": "1073741","uuid": "6ff7ed30-4bb1-4eeb-9e84-b6fa01978d66"}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result": {
        "table_name": "C_Order",
        "id": 1073741,
        "uuid": "43adbe9d-04a7-4cf6-9582-895c1e40da0b"
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/get-private-access

Obtener acceso privado de la tabla y el registro

#### Paràmetros POST:

`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`id` - id del registro.
`uuid` - uuid del registro.

#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/get-private-access?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"table_name": "C_Order","id": "1073741","uuid": "6ff7ed30-4bb1-4eeb-9e84-b6fa01978d66"}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result": {
        "table_name": "C_Order",
        "id": 1073741,
        "uuid": "43adbe9d-04a7-4cf6-9582-895c1e40da0b"
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/get-context-info-value

Obtener información de contexto

#### Paràmetros POST:

`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`uuid` - uuid del registro.
`query` - consulta personalizada en lugar de un nombre de tabla basado en SQL..

#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/get-private-access?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"query": "SELECT * FROM AD_Test","uuid": "771d2187-6103-430a-acfc-aee208f22a0c"}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result": {
        "message_text": "",
        "message_tip": ""
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/list-references

Lista de referencias

#### Paràmetros POST:

`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`id` - id del registro.
`uuid` - uuid del registro.
`windowUuid` - uuid de la ventana
#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/list-references?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"table_name": "C_Order","id": "1073741","uuid": "6ff7ed30-4bb1-4eeb-9e84-b6fa01978d66", "window_uuid": "a52192bc-fb40-11e8-a479-7a0060f0aa01"}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result": {
        "record_count": 0,
        "next_page_token": "",
        "records": [
            {
                "uuid": "42c7a1af-c473-4bf5-83c6-00293b516b98",
                "window_uuid": "a5219852-fb40-11e8-a479-7a0060f0aa01",
                "display_name": "Ver Registros MRP (#1)",
                "table_name": "RV_PP_MRP",
                "where_clause": "(RV_PP_MRP.C_Order_ID=1073741)",
                "record_count": 1
            }
        ]
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/list-browser-items

Lista de elementos del navegador

#### Paràmetros POST:

`uuid` - uuid del buscador.
`parameters` - parametros del buscador
`columns` - columnas de la consulta.
`filters` - filtros de la consulta.
`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`query` - consulta personalizada en lugar de un nombre de tabla basado en SQL.
`where_clause` - cláusula where de la búsqueda basada en SQL.
`order_by_clause` - cláusula order by basada en SQL.
`limit` - límite de registros.
#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/list-browser-items?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"uuid":"8aaefbc2-fb40-11e8-a479-7a0060f0aa01","filters":[{"key":"O_IsSOTrx","value":true,"values":[]},{"key":"O_DocStatus","value":"DR","values":[]}],"query":"SELECT o.Processing AS \"O_Processing\",o.C_Opportunity_ID AS \"O_C_Opportunity_ID\",o.DocStatus AS \"O_DocStatus\",o.DropShip_BPartner_ID AS \"O_DropShip_BPartner_ID\",o.DropShip_Location_ID AS \"O_DropShip_Location_ID\",o.DropShip_User_ID AS \"O_DropShip_User_ID\",o.FreightAmt AS \"O_FreightAmt\",o.IsSelected AS \"O_IsSelected\",o.CopyFrom AS \"O_CopyFrom\",o.IsDelivered AS \"O_IsDelivered\",o.Bill_Location_ID AS \"O_Bill_Location_ID\",o.Pay_BPartner_ID AS \"O_Pay_BPartner_ID\",o.AmountRefunded AS \"O_AmountRefunded\",o.Bill_User_ID AS \"O_Bill_User_ID\",o.Pay_Location_ID AS \"O_Pay_Location_ID\",o.C_Activity_ID AS \"O_C_Activity_ID\",o.C_BPartner_ID AS \"O_C_BPartner_ID\",o.PaymentRule AS \"O_PaymentRule\",o.Posted AS \"O_Posted\",o.DocumentNo AS \"O_DocumentNo\",o.DateOrdered AS \"O_DateOrdered\",o.M_Shipper_ID AS \"O_M_Shipper_ID\",o.M_Warehouse_ID AS \"O_M_Warehouse_ID\",o.OrderType AS \"O_OrderType\",o.AD_Client_ID AS \"O_AD_Client_ID\",o.AD_Org_ID AS \"O_AD_Org_ID\",o.AD_OrgTrx_ID AS \"O_AD_OrgTrx_ID\",o.AD_User_ID AS \"O_AD_User_ID\",o.AmountTendered AS \"O_AmountTendered\",o.Bill_BPartner_ID AS \"O_Bill_BPartner_ID\",o.Weight AS \"O_Weight\",o.C_BPartner_Location_ID AS \"O_C_BPartner_Location_ID\",o.C_Campaign_ID AS \"O_C_Campaign_ID\",o.C_CashLine_ID AS \"O_C_CashLine_ID\",o.C_Charge_ID AS \"O_C_Charge_ID\",o.C_ConversionType_ID AS \"O_C_ConversionType_ID\",o.C_Currency_ID AS \"O_C_Currency_ID\",o.C_DocType_ID AS \"O_C_DocType_ID\",o.C_DocTypeTarget_ID AS \"O_C_DocTypeTarget_ID\",o.ChargeAmt AS \"O_ChargeAmt\",o.C_Order_ID AS \"O_C_Order_ID\",o.C_OrderSource_ID AS \"O_C_OrderSource_ID\",o.C_Payment_ID AS \"O_C_Payment_ID\",o.C_PaymentTerm_ID AS \"O_C_PaymentTerm_ID\",o.C_POS_ID AS \"O_C_POS_ID\",o.C_Project_ID AS \"O_C_Project_ID\",o.Created AS \"O_Created\",o.CreatedBy AS \"O_CreatedBy\",o.DateAcct AS \"O_DateAcct\",o.DatePrinted AS \"O_DatePrinted\",o.DatePromised AS \"O_DatePromised\",o.DeliveryRule AS \"O_DeliveryRule\",o.DeliveryViaRule AS \"O_DeliveryViaRule\",o.Description AS \"O_Description\",o.DocAction AS \"O_DocAction\",o.FreightCostRule AS \"O_FreightCostRule\",o.GrandTotal AS \"O_GrandTotal\",o.InvoiceRule AS \"O_InvoiceRule\",o.UpdatedBy AS \"O_UpdatedBy\",o.IsActive AS \"O_IsActive\",o.IsApproved AS \"O_IsApproved\",o.IsCreditApproved AS \"O_IsCreditApproved\",o.IsDiscountPrinted AS \"O_IsDiscountPrinted\",o.IsDropShip AS \"O_IsDropShip\",o.IsInvoiced AS \"O_IsInvoiced\",o.IsPrinted AS \"O_IsPrinted\",o.IsSelfService AS \"O_IsSelfService\",o.IsSOTrx AS \"O_IsSOTrx\",o.IsTaxIncluded AS \"O_IsTaxIncluded\",o.IsTransferred AS \"O_IsTransferred\",o.Link_Order_ID AS \"O_Link_Order_ID\",o.M_FreightCategory_ID AS \"O_M_FreightCategory_ID\",o.M_PriceList_ID AS \"O_M_PriceList_ID\",o.POReference AS \"O_POReference\",o.PriorityRule AS \"O_PriorityRule\",o.Processed AS \"O_Processed\",o.ProcessedOn AS \"O_ProcessedOn\",o.PromotionCode AS \"O_PromotionCode\",o.Ref_Order_ID AS \"O_Ref_Order_ID\",o.SalesRep_ID AS \"O_SalesRep_ID\",o.SendEMail AS \"O_SendEMail\",o.TotalLines AS \"O_TotalLines\",o.Updated AS \"O_Updated\",o.User1_ID AS \"O_User1_ID\",o.User2_ID AS \"O_User2_ID\",o.Volume AS \"O_Volume\", (SELECT NVL(C_BPartner.Name,'') FROM C_BPartner WHERE o.C_BPartner_ID=C_BPartner.C_BPartner_ID) AS \"DisplayColumn_O_C_BPartner_ID\", C_DocTypeTarget_ID_C_DocType_Trl.Name AS \"DisplayColumn_O_C_DocTypeTarget_ID\", DeliveryRule_AD_Ref_List_Trl.Name AS \"DisplayColumn_O_DeliveryRule\", DocStatus_AD_Ref_List_Trl.Name AS \"DisplayColumn_O_DocStatus\" FROM C_Order o LEFT JOIN C_DocType AS C_DocTypeTarget_ID_C_DocType ON(C_DocTypeTarget_ID_C_DocType.C_DocType_ID = o.C_DocTypeTarget_ID) LEFT JOIN C_DocType_Trl AS C_DocTypeTarget_ID_C_DocType_Trl ON(C_DocTypeTarget_ID_C_DocType_Trl.C_DocType_ID = C_DocTypeTarget_ID_C_DocType.C_DocType_ID AND C_DocTypeTarget_ID_C_DocType_Trl.AD_Language = 'es_VE') LEFT JOIN AD_Ref_List AS DeliveryRule_AD_Ref_List ON(DeliveryRule_AD_Ref_List.Value = o.DeliveryRule AND DeliveryRule_AD_Ref_List.AD_Reference_ID = 151) LEFT JOIN AD_Ref_List_Trl AS DeliveryRule_AD_Ref_List_Trl ON(DeliveryRule_AD_Ref_List_Trl.AD_Ref_List_ID = DeliveryRule_AD_Ref_List.AD_Ref_List_ID AND DeliveryRule_AD_Ref_List_Trl.AD_Language = 'es_VE') LEFT JOIN AD_Ref_List AS DocStatus_AD_Ref_List ON(DocStatus_AD_Ref_List.Value = o.DocStatus AND DocStatus_AD_Ref_List.AD_Reference_ID = 131) LEFT JOIN AD_Ref_List_Trl AS DocStatus_AD_Ref_List_Trl ON(DocStatus_AD_Ref_List_Trl.AD_Ref_List_ID = DocStatus_AD_Ref_List.AD_Ref_List_ID AND DocStatus_AD_Ref_List_Trl.AD_Language = 'es_VE')","where_clause":"o.DocStatus NOT IN('VO')","order_by_clause":""}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result": {
        "record_count": 50,
        "next_page_token": "d3bb9377-b46e-4ec2-96b2-93dd60c71ead-1",
        "records": [
            {
                "id": 0,
                "uuid": "",
                "table_name": "",
                "attributes": [
                    {
                        "key": "DisplayColumn_O_C_BPartner_ID",
                        "value": "INVERSIONES DPJ, C.A"
                    },
                    {
                        "key": "DisplayColumn_O_C_DocTypeTarget_ID",
                        "value": "Orden de Compra Nacional"
                    },
                    {
                        "key": "DisplayColumn_O_DeliveryRule",
                        "value": "Disponibilidad"
                    },
                    {
                        "key": "DisplayColumn_O_DocStatus",
                        "value": "Completo"
                    },
                    {
                        "key": "O_AD_Client_ID",
                        "value": 1000000
                    },
                    {
                        "key": "O_AD_OrgTrx_ID"
                    },
                    {
                        "key": "O_AD_Org_ID",
                        "value": 1000000
                    },
                    {
                        "key": "O_AD_User_ID",
                        "value": 1000437
                    },
                    {
                        "key": "O_AmountRefunded",
                        "value": 0
                    },
                    {
                        "key": "O_AmountTendered",
                        "value": 0
                    },
                    {
                        "key": "O_Bill_BPartner_ID",
                        "value": 1000488
                    },
                    {
                        "key": "O_Bill_Location_ID",
                        "value": 1004666
                    },
                    {
                        "key": "O_Bill_User_ID",
                        "value": 1000437
                    },
                    {
                        "key": "O_C_Activity_ID"
                    },
                    {
                        "key": "O_C_BPartner_ID",
                        "value": 1000488
                    },
                    {
                        "key": "O_C_BPartner_Location_ID",
                        "value": 1004666
                    },
                    {
                        "key": "O_C_Campaign_ID"
                    },
                    {
                        "key": "O_C_CashLine_ID"
                    },
                    {
                        "key": "O_C_Charge_ID"
                    },
                    {
                        "key": "O_C_ConversionType_ID",
                        "value": 1000001
                    },
                    {
                        "key": "O_C_Currency_ID",
                        "value": 50001
                    },
                    {
                        "key": "O_C_DocTypeTarget_ID",
                        "value": 1000119
                    },
                    {
                        "key": "O_C_DocType_ID",
                        "value": 1000119
                    },
                    {
                        "key": "O_C_Opportunity_ID"
                    },
                    {
                        "key": "O_C_OrderSource_ID"
                    },
                    {
                        "key": "O_C_Order_ID",
                        "value": 1056843
                    },
                    {
                        "key": "O_C_POS_ID"
                    },
                    {
                        "key": "O_C_PaymentTerm_ID",
                        "value": 1000000
                    },
                    {
                        "key": "O_C_Payment_ID"
                    },
                    {
                        "key": "O_C_Project_ID"
                    },
                    {
                        "key": "O_ChargeAmt",
                        "value": 0
                    },
                    {
                        "key": "O_CopyFrom"
                    },
                    {
                        "key": "O_Created",
                        "value": "2020-11-17T16:45:44.000Z"
                    },
                    {
                        "key": "O_CreatedBy",
                        "value": 1000387
                    },
                    {
                        "key": "O_DateAcct",
                        "value": "2020-03-01T04:00:00.000Z"
                    },
                    {
                        "key": "O_DateOrdered",
                        "value": "2020-03-01T04:00:00.000Z"
                    },
                    {
                        "key": "O_DatePrinted"
                    },
                    {
                        "key": "O_DatePromised",
                        "value": "2020-11-17T04:00:00.000Z"
                    },
                    {
                        "key": "O_DeliveryRule",
                        "value": "A"
                    },
                    {
                        "key": "O_DeliveryViaRule",
                        "value": "P"
                    },
                    {
                        "key": "O_Description",
                        "value": "MIGRACION CONSIGNACION"
                    },
                    {
                        "key": "O_DocAction"
                    },
                    {
                        "key": "O_DocStatus",
                        "value": "CO"
                    },
                    {
                        "key": "O_DocumentNo",
                        "value": "OCN-1163"
                    },
                    {
                        "key": "O_DropShip_BPartner_ID"
                    },
                    {
                        "key": "O_DropShip_Location_ID"
                    },
                    {
                        "key": "O_DropShip_User_ID"
                    },
                    {
                        "key": "O_FreightAmt",
                        "value": 0
                    },
                    {
                        "key": "O_FreightCostRule",
                        "value": "I"
                    },
                    {
                        "key": "O_GrandTotal",
                        "value": 136276800
                    },
                    {
                        "key": "O_InvoiceRule",
                        "value": "D"
                    },
                    {
                        "key": "O_IsActive",
                        "value": true
                    },
                    {
                        "key": "O_IsApproved",
                        "value": true
                    },
                    {
                        "key": "O_IsCreditApproved",
                        "value": false
                    },
                    {
                        "key": "O_IsDelivered",
                        "value": "Y"
                    },
                    {
                        "key": "O_IsDiscountPrinted",
                        "value": false
                    },
                    {
                        "key": "O_IsDropShip",
                        "value": false
                    },
                    {
                        "key": "O_IsInvoiced",
                        "value": "N"
                    },
                    {
                        "key": "O_IsPrinted",
                        "value": false
                    },
                    {
                        "key": "O_IsSOTrx",
                        "value": false
                    },
                    {
                        "key": "O_IsSelected",
                        "value": false
                    },
                    {
                        "key": "O_IsSelfService",
                        "value": "N"
                    },
                    {
                        "key": "O_IsTaxIncluded",
                        "value": false
                    },
                    {
                        "key": "O_IsTransferred",
                        "value": false
                    },
                    {
                        "key": "O_Link_Order_ID"
                    },
                    {
                        "key": "O_M_FreightCategory_ID"
                    },
                    {
                        "key": "O_M_PriceList_ID",
                        "value": 1000003
                    },
                    {
                        "key": "O_M_Shipper_ID"
                    },
                    {
                        "key": "O_M_Warehouse_ID",
                        "value": 1000002
                    },
                    {
                        "key": "O_OrderType"
                    },
                    {
                        "key": "O_POReference"
                    },
                    {
                        "key": "O_Pay_BPartner_ID"
                    },
                    {
                        "key": "O_Pay_Location_ID"
                    },
                    {
                        "key": "O_PaymentRule",
                        "value": "P"
                    },
                    {
                        "key": "O_Posted"
                    },
                    {
                        "key": "O_PriorityRule",
                        "value": "5"
                    },
                    {
                        "key": "O_Processed",
                        "value": true
                    },
                    {
                        "key": "O_ProcessedOn",
                        "value": 1605631694351.3513
                    },
                    {
                        "key": "O_Processing"
                    },
                    {
                        "key": "O_PromotionCode"
                    },
                    {
                        "key": "O_Ref_Order_ID"
                    },
                    {
                        "key": "O_SalesRep_ID",
                        "value": 1000387
                    },
                    {
                        "key": "O_SendEMail",
                        "value": false
                    },
                    {
                        "key": "O_TotalLines",
                        "value": 117480000
                    },
                    {
                        "key": "O_Updated",
                        "value": "2020-11-17T17:29:42.000Z"
                    },
                    {
                        "key": "O_UpdatedBy",
                        "value": 1000402
                    },
                    {
                        "key": "O_User1_ID"
                    },
                    {
                        "key": "O_User2_ID"
                    },
                    {
                        "key": "O_Volume",
                        "value": 0
                    },
                    {
                        "key": "O_Weight",
                        "value": 0
                    }
                ]
            }
        ]
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/list-lookup-items

Lista de elementos de búsqueda

#### Paràmetros POST:

`filters` - filtros de la consulta.
`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`query` - consulta personalizada en lugar de un nombre de tabla basado en SQL.
`where_clause` - cláusula where de la búsqueda basada en SQL.
`order_by_clause` - cláusula order by basada en SQL.
`limit` - límite de registros.
#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/list-lookup-items?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"table_name":"AD_Ref_List","query":"SELECT NULL, AD_Ref_List.Value,trl.Name, AD_Ref_List.IsActive, AD_Ref_List.UUID FROM AD_Ref_List INNER JOIN AD_Ref_List_Trl trl  ON (AD_Ref_List.AD_Ref_List_ID=trl.AD_Ref_List_ID AND trl.AD_Language='es_VE') WHERE AD_Ref_List.AD_Reference_ID=131 ORDER BY 3","filters":[]}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result": {
        "record_count": 12,
        "next_page_token": "",
        "records": [
            {
                "id": 0,
                "uuid": "a455ffe4-fb40-11e8-a479-7a0060f0aa01",
                "table_name": "",
                "values": {
                    "DisplayColumn": "Anulado",
                    "KeyColumn": "VO",
                    "ValueColumn": "VO"
                }
            },
            {
                "id": 0,
                "uuid": "a455fdb4-fb40-11e8-a479-7a0060f0aa01",
                "table_name": "",
                "values": {
                    "DisplayColumn": "Aprobado",
                    "KeyColumn": "AP",
                    "ValueColumn": "AP"
                }
            },
            {
                "id": 0,
                "uuid": "a459d506-fb40-11e8-a479-7a0060f0aa01",
                "table_name": "",
                "values": {
                    "DisplayColumn": "Borrador",
                    "KeyColumn": "DR",
                    "ValueColumn": "DR"
                }
            },
            {
                "id": 0,
                "uuid": "a455fe36-fb40-11e8-a479-7a0060f0aa01",
                "table_name": "",
                "values": {
                    "DisplayColumn": "Cerrado",
                    "KeyColumn": "CL",
                    "ValueColumn": "CL"
                }
            },
            {
                "id": 0,
                "uuid": "a455fea4-fb40-11e8-a479-7a0060f0aa01",
                "table_name": "",
                "values": {
                    "DisplayColumn": "Completo",
                    "KeyColumn": "CO",
                    "ValueColumn": "CO"
                }
            },
            {
                "id": 0,
                "uuid": "a4560692-fb40-11e8-a479-7a0060f0aa01",
                "table_name": "",
                "values": {
                    "DisplayColumn": "Desconocido",
                    "KeyColumn": "??",
                    "ValueColumn": "??"
                }
            },
            {
                "id": 0,
                "uuid": "a456aec6-fb40-11e8-a479-7a0060f0aa01",
                "table_name": "",
                "values": {
                    "DisplayColumn": "En Proceso",
                    "KeyColumn": "IP",
                    "ValueColumn": "IP"
                }
            },
            {
                "id": 0,
                "uuid": "a46776f2-fb40-11e8-a479-7a0060f0aa01",
                "table_name": "",
                "values": {
                    "DisplayColumn": "Esperando Confirmación",
                    "KeyColumn": "WC",
                    "ValueColumn": "WC"
                }
            },
            {
                "id": 0,
                "uuid": "a459d308-fb40-11e8-a479-7a0060f0aa01",
                "table_name": "",
                "values": {
                    "DisplayColumn": "Esperando Pago",
                    "KeyColumn": "WP",
                    "ValueColumn": "WP"
                }
            },
            {
                "id": 0,
                "uuid": "a459d290-fb40-11e8-a479-7a0060f0aa01",
                "table_name": "",
                "values": {
                    "DisplayColumn": "No Aprobado",
                    "KeyColumn": "NA",
                    "ValueColumn": "NA"
                }
            },
            {
                "id": 0,
                "uuid": "a455ff08-fb40-11e8-a479-7a0060f0aa01",
                "table_name": "",
                "values": {
                    "DisplayColumn": "No-Válido",
                    "KeyColumn": "IN",
                    "ValueColumn": "IN"
                }
            },
            {
                "id": 0,
                "uuid": "a455ff76-fb40-11e8-a479-7a0060f0aa01",
                "table_name": "",
                "values": {
                    "DisplayColumn": "Reversado",
                    "KeyColumn": "RE",
                    "ValueColumn": "RE"
                }
            }
        ]
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/get-lookup-item

Obtener elemento de búsqueda

#### Paràmetros POST:

`filters` - filtros de la consulta.
`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`query` - consulta personalizada en lugar de un nombre de tabla basado en SQL.
`where_clause` - cláusula where de la búsqueda basada en SQL.
`order_by_clause` - cláusula order by basada en SQL.
`limit` - límite de registros.
#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/get-lookup-item?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"table_name":"AD_Ref_List","query":"SELECT NULL, AD_Ref_List.Value,trl.Name, AD_Ref_List.IsActive, AD_Ref_List.UUID FROM AD_Ref_List INNER JOIN AD_Ref_List_Trl trl  ON (AD_Ref_List.AD_Ref_List_ID=trl.AD_Ref_List_ID AND trl.AD_Language='es_VE') WHERE AD_Ref_List.AD_Reference_ID=131 ORDER BY 3","filters":[]}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result": {
        "id": 0,
        "uuid": "a455ffe4-fb40-11e8-a479-7a0060f0aa01",
        "table_name": "",
        "values": {
            "DisplayColumn": "Anulado",
            "KeyColumn": "VO",
            "ValueColumn": "VO"
        }
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/list-translations

Lista de traducciones

#### Paràmetros POST:

`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`id` - id de referencia.
`uuid` - uuid de referencia.
#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/list-translations?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"table_name": "AD_View","id": "50000","uuid": "a4cb498e-fb40-11e8-a479-7a0060f0aa01"}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200,
    "result": {
        "record_count": 0,
        "next_page_token": "",
        "records": [
            {
                "language": "es_VE",
                "uuid": "",
                "values": {
                    "Description": "Allow select the Sales Order lines to create a Outbound Order",
                    "Name": "Sales Order to Picking"
                }
            }
        ]
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/get-default-value

Obtener valor por defecto

#### Paràmetros POST:

`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`query` - consulta personalizada en lugar de un nombre de tabla basado en SQL.
#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/get-default-value?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"query": "SELECT Name from AD_TEST WHERE IsActive = 'Y' AND (SELECT MAX(AD_TEST_ID) FROM AD_TEST)"}'
```
#### Cuerpo de Respuesta:

```json
{
    "code": 200
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error

### POST /adempiere-api/ui/run-callout

Ejecutar llamada

#### Paràmetros POST:

`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`tab_uuid` - uuid de la pestaña.
`windowUuid` - uuid de la ventana.
`callout` - llamada.
`columnName` - nombre de la columna de la llamada.
`old_value` - valor antiguo para la columna.
`value` - nuevo valor de  la columna.
`window_no` - número de ventana.
`attributes` - atributos de la entidad.
#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/run-callout?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"tableName": "AD_TEST","windowUuid": "771d2187-6103-430a-acfc-aee208f22a0c","callout": "INSERT","columnName": "IsActive","oldValue": false,"value": true,"tabUuid": "987d2187-6103-430a-acfc-aee208f22a0c","windowNo": 2,"attributesList": []}'
    
```
#### Cuerpo de Respuesta:

```json 
{
    "code": 500,
    "result": {
        "created": "2020-09-18T17:22:59-04:30",
        "id": 10,
        "uuid": "771d2187-6103-430a-acfc-aee208f22a0c",
        "name": "Test Name",
        "description": "Test Description",
        "help": "Test Help",
        "IsProcessed": true,
        "isActive": true
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error


### POST /adempiere-api/ui/rollback-entity

Obtener información de contexto

#### Paràmetros POST:

`table_name` - nombre de la tabla (obligatorio si no es una consulta).
`id` - id de referencia.
`uuid` - uuid de referencia.
#### Cuerpo de la Petición:

```json
{
	"token": "5339c283-dc77-4001-8315-22905596d6c0",
    "language": "es"
}
```

#### Ejemplo de Llamada:

```bash
curl 'https://api.erpya.com/adempiere-api/ui/rollback-entity?token=9938867d-b2c5-45bc-8650-c2b484b4887f&language=es'\
    -X POST \
    -H 'content-type: application/json' \
    -H 'accept: */*;charset=UTF-8'
    --data-binary '{"tableName": "AD_TEST","id": 15,"uuid": "771d2187-6103-430a-acfc-aee208f22a0c"}'
    
```
#### Cuerpo de Respuesta:

```json
{
    "code": 500,
    "result": {
        "created": "2020-09-18T17:22:59-04:30",
        "id": 10,
        "uuid": "771d2187-6103-430a-acfc-aee208f22a0c",
        "name": "Test Name",
        "description": "Test Description",
        "help": "Test Help",
        "IsProcessed": true,
        "isActive": true
    }
}
```
#### Código de Respuesta:

- `200` cuando es exitoso
- `500` en caso de error