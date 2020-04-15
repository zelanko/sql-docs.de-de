---
title: Erstellen von SQL Server-Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- SQL Server Native Client OLE DB provider, tables
- DBCOLUMNDESC usage
- adding tables
- CreateTable function
ms.assetid: a7b8d142-d76a-44d9-a583-86ac5109fbe8
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6f3d1ae29828e18cf98941666e7884e70115ba39
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301861"
---
# <a name="creating-sql-server-tables"></a>Erstellen von SQL Server-Tabellen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter macht die **Funktion ITableDefinition::CreateTable** verfügbar, sodass Verbraucher Tabellen erstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können. Consumer verwenden **CreateTable,** um permanente Tabellen mit Consumernamen und permanente oder temporäre Tabellen mit eindeutigen Namen zu erstellen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vom nativen Client-OLE-DB-Anbieter generiert werden.  
  
 Wenn der Consumer **ITableDefinition::CreateTable**aufruft, wenn der Wert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der DBPROP_TBL_TEMPTABLE-Eigenschaft VARIANT_TRUE ist, generiert der native Client-OLE-DB-Anbieter einen temporären Tabellennamen für den Consumer. Der Consumer legt den *pTableID*-Parameter der **CreateTable**-Methode auf NULL fest. Die temporären Tabellen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Namen, die vom nativen Client-OLE-DB-Anbieter generiert werden, werden nicht im **Tabellenrowset** angezeigt, sind jedoch über die **IOpenRowset-Schnittstelle** zugänglich.  
  
 Wenn Consumer den Tabellennamen im *pwszName-Member* der *uName-Union* im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *pTableID-Parameter* angeben, erstellt der native Client-OLE-DB-Anbieter eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle mit diesem Namen. Es gelten die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Einschränkungen für Tabellennamen, und der Tabellenname kann eine dauerhafte Tabelle angeben oder entweder eine lokale oder globale temporäre Tabelle. Weitere Informationen finden Sie unter [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md). Der *ppTableID*-Parameter kann NULL sein.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter kann die Namen permanenter oder temporärer Tabellen generieren. Wenn der Consumer den *pTableID-Parameter* auf NULL und *ppTableID* so\*festlegt, dass er auf einen gültigen DBID zeigt, gibt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter den generierten Namen der Tabelle im *pwszName-Member* der *uName-Union* der DBID zurück, auf den der Wert von *ppTableID*verwiesen wird. Um eine temporäre, mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] System-OLE-DB-Anbieter benannte Tabelle zu erstellen, schließt der Consumer die OLE DB-Tabelleneigenschaft DBPROP_TBL_TEMPTABLE in einen Tabelleneigenschaftensatz ein, auf den im Parameter *rgPropertySets* verwiesen wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Temporäre Tabellen mit dem Namen "Native Client OLE DB" mit namenlosem Clientsystem sind lokal.  
  
 **CreateTable** gibt DB_E_BADTABLEID zurück, wenn das *eKind*-Element des *pTableID*-Parameters nicht DBKIND_NAME angibt.  
  
## <a name="dbcolumndesc-usage"></a>DBCOLUMNDESC-Verwendung  
 Der Consumer kann einen Spaltendatentyp durch Verwendung des *pwszTypeName*-Elements oder des *wType*-Elements angeben. Wenn der Consumer den Datentyp in *pwszTypeName*angibt, ignoriert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter den Wert von *wType*.  
  
 Bei Verwendung des *pwszTypeName*-Elements gibt der Consumer den Datentyp mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypnamen an. Gültige Datentypnamen sind die, die in der Spalte TYPE_NAME des PROVIDER_TYPES-Schemarowsets zurückgegeben werden.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter erkennt eine Teilmenge der OLE DB-aufgezählten DBTYPE-Werte im *wType-Member.* Weitere Informationen finden Sie unter [Datentypzuordnung in ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).  
  
> [!NOTE]  
>  **CreateTable** gibt DB_E_BADTYPE zurück, wenn der Consumer das *pTypeInfo*- oder *pclsid*-Element zur Angabe des Spaltendatentyps verwendet.  
  
 Der Consumer gibt dne Spaltennamen im *pwszName*-Element der *uName*-Union des DBCOLUMNDESC *dbcid*-Elements an. Der Spaltenname wird als Unicode-Zeichenfolge angegeben. Das *eKind*-Element von *dbcid* muss DBKIND_NAME sein. **CreateTable** gibt DB_E_BADCOLUMNID zurück, wenn *eKind* ungültig ist,*pwszName* NULL ist oder der Wert von *pwszName* kein gültiger [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Bezeichner ist.  
  
 Alle Spalteneigenschaften sind in allen für die Tabelle definierten Spalten verfügbar. **CreateTable** kann DB_S_ERRORSOCCURRED oder DB_E_ERRORSOCCURRED zurückgeben, wenn Eigenschaftenwerte zu Konflikten führen. **CreateTable** gibt einen Fehler zurück, wenn ungültige Spalteneigenschaften Fehler bei der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabellenerstellung verursachen.  
  
 Spalteneigenschaften in DBCOLUMNDESC werden wie folgt interpretiert.  
  
|Eigenschafts-ID|Beschreibung|  
|-----------------|-----------------|  
|DBPROP_COL_AUTOINCREMENT|R/W: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE-Beschreibung: Legt die IDENTITY-Eigenschaft der Spalte, die erstellt wird, fest. Für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist die IDENTITY-Eigenschaft für eine einzelne Spalte innerhalb einer Tabelle gültig. Wenn Sie die Eigenschaft auf VARIANT_TRUE für mehr [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als eine einzelne Spalte festlegen, wird ein Fehler generiert, wenn der native Client-OLE-DB-Anbieter versucht, die Tabelle auf dem Server zu erstellen.<br /><br /> Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Identitätseigenschaft ist nur für **integer**-, **numeric**- und **decimal**-Typen gültig wenn der Dezimalstellenwert 0 (null) ist. Wenn Sie die Eigenschaft auf VARIANT_TRUE für eine Spalte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eines anderen Datentyps festlegen, wird ein Fehler generiert, wenn der native Client-OLE-DB-Anbieter versucht, die Tabelle auf dem Server zu erstellen.<br /><br /> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt DB_S_ERRORSOCCURRED zurück, wenn DBPROP_COL_AUTOINCREMENT und DBPROP_COL_NULLABLE VARIANT_TRUE sind und die *dwOption* von DBPROP_COL_NULLABLE nicht DBPROPOPTIONS_REQUIRED ist. DB_E_ERRORSOCCURRED wird zurückgegeben, wenn sowohl DBPROP_COL_AUTOINCREMENT als auch DBPROP_COL_NULLABLE den Wert VARIANT_TRUE haben und *dwOption* von DBPROP_COL_NULLABLE gleich DBPROPOPTIONS_REQUIRED ist. Die Spalte wird mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Identitätseigenschaft definiert, und das DBPROP_COL_NULLABLE *dwStatus*-Element wird auf DBPROPSTATUS_CONFLICTING festgelegt.|  
|DBPROP_COL_DEFAULT|R/W: Lesen/Schreiben<br /><br /> Standardwert: Keiner<br /><br /> Beschreibung: Erstellt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DEFAULT-Einschränkung für die Spalte.<br /><br /> Das *vValue* DBPROP-Element kann verschiedenen Typen entsprechen. Das *vValue.vt*-Element sollte einen Typ angeben, der mit dem Datentyp der Spalte kompatibel ist. Beispielsweise ist BSTR N/A als Standardwert für eine Spalte geeignet, die als DBTYPE_WSTR definiert ist. Das Definieren derselben Standardeinstellung für eine Spalte, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die als DBTYPE_R8 definiert ist, generiert einen Fehler, wenn der native Client-OLE-DB-Anbieter versucht, die Tabelle auf dem Server zu erstellen.|  
|DBPROP_COL_DESCRIPTION|R/W: Lesen/Schreiben<br /><br /> Standardwert: Keiner<br /><br /> Beschreibung: Die DBPROP_COL_DESCRIPTION-Spalteneigenschaft wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vom Native Client OLE DB-Anbieter nicht implementiert.<br /><br /> Das *dwStatus*-Element der DBPROP-Struktur gibt DBPROPSTATUS_NOTSUPPORTED zurück, wenn der Consumer versucht, den Eigenschaftenwert zu schreiben.<br /><br /> Das Festlegen der Eigenschaft stellt für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Native Client OLE DB-Anbieter keinen schwerwiegenden Fehler dar. Wenn alle anderen Parameterwerte gültig sind, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle erstellt.|  
|DBPROP_COL_FIXEDLENGTH|R/W: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE<br /><br /> Beschreibung: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Der native Client-OLE-DB-Anbieter verwendet DBPROP_COL_FIXEDLENGTH, um die Datentypzuordnung zu bestimmen, wenn der Consumer den Datentyp einer Spalte mithilfe des *wType-Members* des DBCOLUMNDESC definiert. Weitere Informationen finden Sie unter [Datentypzuordnung in ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).|  
|DBPROP_COL_NULLABLE|R/W: Lesen/Schreiben<br /><br /> Standardwert: Keiner<br /><br /> Beschreibung: Beim Erstellen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle gibt der native Client-OLE-DB-Anbieter an, ob die Spalte NULL-Werte akzeptieren soll, wenn die Eigenschaft festgelegt ist. Ist die Eigenschaft nicht festgelegt, wird durch die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ANSI_NULLS-Standarddatenbankoption festgelegt, ob die Spalte NULL-Werte akzeptiert.<br /><br /> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ist ein ISO-kompatibler Anbieter. Verbundene Sitzungen weisen ISO-Verhalten auf. Wenn der Consumer DBPROP_COL_NULLABLE nicht festlegt, akzeptieren die Spalten NULL-Werte.|  
|DBPROP_COL_PRIMARYKEY|R/W: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE Beschreibung: Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VARIANT_TRUE, erstellt der native Client-OLE-DB-Anbieter die Spalte mit einer PRIMARY KEY-Einschränkung.<br /><br /> Wenn sie als Spalteneigenschaft definiert ist, kann nur eine einzelne Spalte die Einschränkung bestimmen. Das Festlegen der Eigenschaft VARIANT_TRUE für mehr als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine einzelne Spalte gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Fehler zurück, wenn der native Client-OLE-DB-Anbieter versucht, die Tabelle zu erstellen.<br /><br /> Hinweis: Der Consumer kann **IIndexDefinition::CreateIndex** verwenden, um eine PRIMARY KEY-Einschränkung für zwei oder mehr Spalten zu erstellen.<br /><br /> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt DB_S_ERRORSOCCURRED zurück, wenn DBPROP_COL_PRIMARYKEY und DBPROP_COL_UNIQUE sowohl VARIANT_TRUE als auch die *dwOption* von DBPROP_COL_UNIQUE nicht DBPROPOPTIONS_REQUIRED ist.<br /><br /> DB_E_ERRORSOCCURRED wird zurückgegeben, wenn sowohl DBPROP_COL_PRIMARYKEY als auch DBPROP_COL_UNIQUE den Wert VARIANT_TRUE haben und *dwOption* von DBPROP_COL_UNIQUE gleich DBPROPOPTIONS_REQUIRED ist. Die Spalte wird mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Identitätseigenschaft definiert, und das DBPROP_COL_PRIMARYKEY *dwStatus*-Element wird auf DBPROPSTATUS_CONFLICTING festgelegt.<br /><br /> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt einen Fehler zurück, wenn DBPROP_COL_PRIMARYKEY und DBPROP_COL_NULLABLE VARIANT_TRUE sind.<br /><br /> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt einen Fehler zurück, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Consumer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versucht, eine PRIMARY KEY-Einschränkung für eine Spalte mit ungültigen Datentypen zu erstellen. PRIMARY KEY-Einschränkungen können nicht für Spalten definiert werden, die mit den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen **bit**, **text**, **ntext** und **image** erstellt wurden.|  
|DBPROP_COL_UNIQUE|R/W: Lesen/Schreiben<br /><br /> Standardwert: VARIANT_FALSE Beschreibung: Wendet eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UNIQUE-Einschränkung auf die Spalte an.<br /><br /> Wenn sie als Spalteneigenschaft definiert ist, wird die Einschränkung nur auf eine einzelne Spalte angewendet. Der Consumer kann **IIndexDefinition::CreateIndex** verwenden, um eine UNIQUE-Einschränkung auf kombinierte Werte von zwei oder mehr Spalten anzuwenden.<br /><br /> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt DB_S_ERRORSOCCURRED zurück, wenn DBPROP_COL_PRIMARYKEY und DBPROP_COL_UNIQUE VARIANT_TRUE und *dwOption* nicht DBPROPOPTIONS_REQUIRED sind.<br /><br /> DB_E_ERRORSOCCURRED wird zurückgegeben, wenn sowohl DBPROP_COL_PRIMARYKEY als auch DBPROP_COL_UNIQUE den Wert VARIANT_TRUE haben und *dwOption* gleich DBPROPOPTIONS_REQUIRED ist. Die Spalte wird mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Identitätseigenschaft definiert, und das DBPROP_COL_PRIMARYKEY *dwStatus*-Element wird auf DBPROPSTATUS_CONFLICTING festgelegt.<br /><br /> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt DB_S_ERRORSOCCURRED zurück, wenn DBPROP_COL_NULLABLE und DBPROP_COL_UNIQUE VARIANT_TRUE und *dwOption* nicht DBPROPOPTIONS_REQUIRED sind.<br /><br /> DB_E_ERRORSOCCURRED wird zurückgegeben, wenn sowohl DBPROP_COL_NULLABLE als auch DBPROP_COL_UNIQUE den Wert VARIANT_TRUE haben und *dwOption* gleich DBPROPOPTIONS_REQUIRED ist. Die Spalte wird mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Identitätseigenschaft definiert, und das DBPROP_COL_NULLABLE *dwStatus*-Element wird auf DBPROPSTATUS_CONFLICTING festgelegt.<br /><br /> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt einen Fehler zurück, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consumer versucht, eine UNIQUE-Einschränkung für eine Spalte mit ungültigen Datentypen zu erstellen. UNIQUE-Einschränkungen können nicht für Spalten definiert werden, die mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bit**-Datentyp erstellt wurden.|  
  
 Wenn der Consumer **ITableDefinition::CreateTable**aufruft, interpretiert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter Tabelleneigenschaften wie folgt.  
  
|Eigenschafts-ID|Beschreibung|  
|-----------------|-----------------|  
|DBPROP_TBL_TEMPTABLE|R/W: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE Beschreibung: Standardmäßig [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt der native Client-OLE-DB-Anbieter Tabellen, die vom Consumer benannt werden. Wenn VARIANT_TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generiert der native Client-OLE-DB-Anbieter einen temporären Tabellennamen für den Consumer. Der Consumer legt den *pTableID*-Parameter von **CreateTable** auf NULL fest. Der *ppTableID*-Parameter muss einen gültigen Zeiger enthalten.|  
  
 Wenn der Consumer anfordert, dass ein Rowset [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für eine erfolgreich erstellte Tabelle geöffnet wird, öffnet der native Client-OLE-DB-Anbieter ein cursorunterstütztes Rowset. Alle Rowseteigenschaften können in den übergebenen Eigenschaftensätzen angegeben werden.  
  
 Mit diesem Beispiel wird eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle erstellt.  
  
```  
// This CREATE TABLE statement shows the details of the table created by   
// the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//    CONSTRAINT PK_OrderDetails  
//         PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
// The PRIMARY KEY constraint is created in an additional example.  
HRESULT CreateTable  
    (  
    ITableDefinition* pITableDefinition  
    )  
    {  
    DBID            dbidTable;  
    const ULONG     nCols = 5;  
    ULONG           nCol;  
    ULONG           nProp;  
    DBCOLUMNDESC    dbcoldesc[nCols];  
  
    HRESULT         hr;  
  
    // Set up column descriptions. First, set default property values for  
    //  the columns.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbcoldesc[nCol].pwszTypeName = NULL;  
        dbcoldesc[nCol].pTypeInfo = NULL;  
        dbcoldesc[nCol].rgPropertySets = new DBPROPSET;  
        dbcoldesc[nCol].pclsid = NULL;  
        dbcoldesc[nCol].cPropertySets = 1;  
        dbcoldesc[nCol].ulColumnSize = 0;  
        dbcoldesc[nCol].dbcid.eKind = DBKIND_NAME;  
        dbcoldesc[nCol].wType = DBTYPE_I4;  
        dbcoldesc[nCol].bPrecision = 0;  
        dbcoldesc[nCol].bScale = 0;  
  
        dbcoldesc[nCol].rgPropertySets[0].rgProperties =   
            new DBPROP[NCOLPROPS_MAX];  
        dbcoldesc[nCol].rgPropertySets[0].cProperties = NCOLPROPS_MAX;  
        dbcoldesc[nCol].rgPropertySets[0].guidPropertySet =  
            DBPROPSET_COLUMN;  
  
        for (nProp = 0; nProp < NCOLPROPS_MAX; nProp++)  
            {  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                dwOptions = DBPROPOPTIONS_REQUIRED;  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].colid  
                 = DB_NULLID;  
  
            VariantInit(  
                &(dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                    vValue));  
  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                vValue.vt = VT_BOOL;  
            }  
        }  
  
    // Set the column-specific information.  
    dbcoldesc[0].dbcid.uName.pwszName = L"OrderID";  
    dbcoldesc[0].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[0].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[0].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[1].dbcid.uName.pwszName = L"ProductID";  
    dbcoldesc[1].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[1].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[1].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[2].dbcid.uName.pwszName = L"UnitPrice";  
    dbcoldesc[2].wType = DBTYPE_CY;  
    dbcoldesc[2].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[2].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[2].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[3].dbcid.uName.pwszName = L"Quantity";  
    dbcoldesc[3].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[3].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[3].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[4].dbcid.uName.pwszName = L"Discount";  
    dbcoldesc[4].wType = DBTYPE_NUMERIC;  
    dbcoldesc[4].bPrecision = 2;  
    dbcoldesc[4].bScale = 2;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].dwPropertyID =   
        DBPROP_COL_DEFAULT;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].vValue.vt = VT_BSTR;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].vValue.bstrVal =  
        SysAllocString(L"0");  
    dbcoldesc[4].rgPropertySets[0].cProperties = 2;  
  
    // Set up the dbid for OrderDetails.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    if (FAILED(hr = pITableDefinition->CreateTable(NULL, &dbidTable,  
        nCols, dbcoldesc, NULL, 0, NULL, NULL, NULL)))  
        {  
        DumpError(pITableDefinition, IID_ITableDefinition);  
        goto SAFE_EXIT;  
        }  
  
SAFE_EXIT:  
    // Clean up dynamic allocation in the property sets.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        for (nProp = 0; nProp < NCOLPROPS_MAX; nProp++)  
            {  
            if (dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                vValue.vt == VT_BSTR)  
                {  
                SysFreeString(dbcoldesc[nCol].rgPropertySets[0].  
                    rgProperties[nProp].vValue.bstrVal);  
                }  
            }  
  
        delete [] dbcoldesc[nCol].rgPropertySets[0].rgProperties;  
        delete [] dbcoldesc[nCol].rgPropertySets;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellen und Indizes](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
