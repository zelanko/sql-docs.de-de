---
title: Erstellen von SQL Server-Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e780a04f59bacba5063ac0bd6e9b7f3c74fd211a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086750"
---
# <a name="creating-sql-server-tables"></a>Erstellen von SQL Server-Tabellen
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die **itabledefinition:: CreateTable** -Funktion ermöglicht es Consumern, erstellen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen. Consumer verwenden **CreateTable** zum Erstellen von dauerhaften Tabellen Consumer benannt und dauerhaften oder temporären Tabellen eindeutige Namen durch die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter.  
  
 Wenn der Consumer ruft **itabledefinition:: CreateTable**, wenn der Wert der Eigenschaft DBPROP_TBL_TEMPTABLE VARIANT_TRUE ist, ist die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter generiert einen temporären Tabellennamen für den Consumer. Der Consumer legt den *pTableID*-Parameter der **CreateTable**-Methode auf NULL fest. Die temporären Tabellen mit Namen, die vom der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter werden nicht in der **Tabellen** Rowset, jedoch können Sie über die **IOpenRowset** Schnittstelle.  
  
 Wenn Consumer geben den Tabellennamen in der *PwszName* Mitglied der *uName* -Vereinigung der *pTableID* -Parameter der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erstellt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle mit diesem Namen. Es gelten die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Einschränkungen für Tabellennamen, und der Tabellenname kann eine dauerhafte Tabelle angeben oder entweder eine lokale oder globale temporäre Tabelle. Weitere Informationen finden Sie unter [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql). Der *ppTableID*-Parameter kann NULL sein.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter kann die Namen dauerhafter oder temporärer Tabellen generieren. Wenn der Consumer legt den *pTableID* Parameter auf NULL und legt *PpTableID* , zeigen Sie auf eine gültige DBID\*, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt zurück, der generierte Name der der Tabelle die *PwszName* Mitglied der *uName* Kombination der DBID zeigt den Wert der *PpTableID*. Erstellen einen temporären, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter benannte Tabelle, schließt der Consumer die OLE DB-Tabelleneigenschaft DBPROP_TBL_TEMPTABLE in einen tabelleneigenschaftensatz verwiesen wird, in der *RgPropertySets* Parameter. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter benannte temporäre Tabellen sind lokal.  
  
 **CreateTable** gibt DB_E_BADTABLEID zurück, wenn das *eKind*-Element des *pTableID*-Parameters nicht DBKIND_NAME angibt.  
  
## <a name="dbcolumndesc-usage"></a>DBCOLUMNDESC-Verwendung  
 Der Consumer kann einen Spaltendatentyp durch Verwendung des *pwszTypeName*-Elements oder des *wType*-Elements angeben. Wenn der Consumer den Datentyp in gibt *PwszTypeName*, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ignoriert den Wert der *wType*.  
  
 Bei Verwendung des *pwszTypeName*-Elements gibt der Consumer den Datentyp mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypnamen an. Gültige Datentypnamen sind die, die in der Spalte TYPE_NAME des PROVIDER_TYPES-Schemarowsets zurückgegeben werden.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erkennt eine Teilmenge der OLE DB aufgelisteten DBTYPE-Werten in der *wType* Member. Weitere Informationen finden Sie unter [Data Type Mapping itabledefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).  
  
> [!NOTE]  
>  **CreateTable** gibt DB_E_BADTYPE zurück, wenn der Consumer das *pTypeInfo*- oder *pclsid*-Element zur Angabe des Spaltendatentyps verwendet.  
  
 Der Consumer gibt dne Spaltennamen im *pwszName*-Element der *uName*-Union des DBCOLUMNDESC *dbcid*-Elements an. Der Spaltenname wird als Unicode-Zeichenfolge angegeben. Das *eKind*-Element von *dbcid* muss DBKIND_NAME sein. **CreateTable** gibt DB_E_BADCOLUMNID zurück, wenn *eKind* ungültig ist,*pwszName* NULL ist oder der Wert von *pwszName* kein gültiger [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Bezeichner ist.  
  
 Alle Spalteneigenschaften sind in allen für die Tabelle definierten Spalten verfügbar. **CreateTable** kann DB_S_ERRORSOCCURRED oder DB_E_ERRORSOCCURRED zurückgeben, wenn Eigenschaftenwerte zu Konflikten führen. **CreateTable** gibt einen Fehler zurück, wenn ungültige Spalteneigenschaften Fehler bei der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabellenerstellung verursachen.  
  
 Spalteneigenschaften in DBCOLUMNDESC werden wie folgt interpretiert.  
  
|Eigenschafts-ID|Description|  
|-----------------|-----------------|  
|DBPROP_COL_AUTOINCREMENT|R/W: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE-Beschreibung: Legt die IDENTITY-Eigenschaft der Spalte, die erstellt wird, fest. Für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist die IDENTITY-Eigenschaft für eine einzelne Spalte innerhalb einer Tabelle gültig. Festlegen der Eigenschaft auf VARIANT_TRUE fest, für mehr als eine einzelne Spalte einen Fehler generiert. wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter versucht, in der Tabelle auf dem Server zu erstellen.<br /><br /> Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Identitätseigenschaft ist nur für **integer**-, **numeric**- und **decimal**-Typen gültig wenn der Dezimalstellenwert 0 (null) ist. Festlegen der Eigenschaft auf VARIANT_TRUE fest, für eine Spalte mit einem beliebigen anderen Datentyp wird ein Fehler generiert, wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter versucht, in der Tabelle auf dem Server zu erstellen.<br /><br /> Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt DB_S_ERRORSOCCURRED zurück, wenn DBPROP_COL_AUTOINCREMENT als auch DBPROP_COL_NULLABLE den Wert VARIANT_TRUE haben und die *DwOption* von DBPROP_COL_NULLABLE ist nicht DBPROPOPTIONS_ Erforderlich. DB_E_ERRORSOCCURRED wird zurückgegeben, wenn sowohl DBPROP_COL_AUTOINCREMENT als auch DBPROP_COL_NULLABLE den Wert VARIANT_TRUE haben und *dwOption* von DBPROP_COL_NULLABLE gleich DBPROPOPTIONS_REQUIRED ist. Die Spalte wird mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Identitätseigenschaft definiert, und das DBPROP_COL_NULLABLE *dwStatus*-Element wird auf DBPROPSTATUS_CONFLICTING festgelegt.|  
|DBPROP_COL_DEFAULT|R/W: Lesen/Schreiben<br /><br /> Standardwert: Keiner<br /><br /> Beschreibung: Erstellt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DEFAULT-Einschränkung für die Spalte.<br /><br /> Das *vValue* DBPROP-Element kann verschiedenen Typen entsprechen. Das *vValue.vt*-Element sollte einen Typ angeben, der mit dem Datentyp der Spalte kompatibel ist. Beispielsweise ist BSTR N/A als Standardwert für eine Spalte geeignet, die als DBTYPE_WSTR definiert ist. Definieren die gleiche Standard für eine Spalte, die als DBTYPE_R8 einen Fehler generiert definiert bei der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter versucht, in der Tabelle auf dem Server zu erstellen.|  
|DBPROP_COL_DESCRIPTION|R/W: Lesen/Schreiben<br /><br /> Standardwert: Keiner<br /><br /> Beschreibung: Die Spalteneigenschaft dbprop_col_description wird nicht von implementiert die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter.<br /><br /> Das *dwStatus*-Element der DBPROP-Struktur gibt DBPROPSTATUS_NOTSUPPORTED zurück, wenn der Consumer versucht, den Eigenschaftenwert zu schreiben.<br /><br /> Festlegen der Eigenschaft wird, keinen schwerwiegenden Fehler für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter. Wenn alle anderen Parameterwerte gültig sind, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle erstellt.|  
|DBPROP_COL_FIXEDLENGTH|R/W: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE<br /><br /> Beschreibung: Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verwendet DBPROP_COL_FIXEDLENGTH, um die datentypzuordnung zu bestimmen, wenn der Consumer einen Spaltendatentyp mithilfe von definiert die *wType* Mitglied der dbcolumndesc-Struktur. Weitere Informationen finden Sie unter [Data Type Mapping itabledefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).|  
|DBPROP_COL_NULLABLE|R/W: Lesen/Schreiben<br /><br /> Standardwert: Keiner<br /><br /> Beschreibung: Beim Erstellen der Tabelle, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt an, ob die Spalte Nullwerte akzeptieren soll, wenn die Eigenschaft festgelegt ist. Ist die Eigenschaft nicht festgelegt, wird durch die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ANSI_NULLS-Standarddatenbankoption festgelegt, ob die Spalte NULL-Werte akzeptiert.<br /><br /> Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ist ein ISO-kompatiblen Anbieter. Verbundene Sitzungen weisen ISO-Verhalten auf. Wenn der Consumer DBPROP_COL_NULLABLE nicht festlegt, akzeptieren die Spalten NULL-Werte.|  
|DBPROP_COL_PRIMARYKEY|R/W: Lesen/Schreiben<br /><br /> Standardwert: VARIANT_FALSE Beschreibung: Wenn VARIANT_TRUE ist, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erstellt die Spalte mit einer PRIMARY KEY-Einschränkung.<br /><br /> Wenn sie als Spalteneigenschaft definiert ist, kann nur eine einzelne Spalte die Einschränkung bestimmen. Festlegen der Eigenschaft VARIANT_TRUE für mehr als eine einzelne Spalte einen Fehler zurückgibt, wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter versucht, erstellen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle.<br /><br /> Hinweis: Der Consumer kann **IIndexDefinition::CreateIndex** verwenden, um eine PRIMARY KEY-Einschränkung für zwei oder mehr Spalten zu erstellen.<br /><br /> Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt DB_S_ERRORSOCCURRED zurück, wenn sowohl DBPROP_COL_PRIMARYKEY als auch dbprop_col_unique den Wert VARIANT_TRUE haben und die *DwOption* von DBPROP_COL_UNIQUE nicht DBPROPOPTIONS_REQUIRED ist.<br /><br /> DB_E_ERRORSOCCURRED wird zurückgegeben, wenn sowohl DBPROP_COL_PRIMARYKEY als auch DBPROP_COL_UNIQUE den Wert VARIANT_TRUE haben und *dwOption* von DBPROP_COL_UNIQUE gleich DBPROPOPTIONS_REQUIRED ist. Die Spalte wird mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Identitätseigenschaft definiert, und das DBPROP_COL_PRIMARYKEY *dwStatus*-Element wird auf DBPROPSTATUS_CONFLICTING festgelegt.<br /><br /> Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt einen Fehler zurück, wenn sowohl DBPROP_COL_PRIMARYKEY als auch DBPROP_COL_NULLABLE den Wert VARIANT_TRUE haben.<br /><br /> Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt einen Fehler von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Wenn der Consumer versucht, zum Erstellen einer PRIMARY KEY-Einschränkung für eine Spalte ungültig [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp. PRIMARY KEY-Einschränkungen können nicht für Spalten definiert werden, die mit den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen **bit**, **text**, **ntext** und **image** erstellt wurden.|  
|DBPROP_COL_UNIQUE|R/W: Lesen/Schreiben<br /><br /> Standardwert: VARIANT_FALSE Beschreibung: Wendet eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UNIQUE-Einschränkung auf die Spalte an.<br /><br /> Wenn sie als Spalteneigenschaft definiert ist, wird die Einschränkung nur auf eine einzelne Spalte angewendet. Der Consumer kann **IIndexDefinition::CreateIndex** verwenden, um eine UNIQUE-Einschränkung auf kombinierte Werte von zwei oder mehr Spalten anzuwenden.<br /><br /> Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt DB_S_ERRORSOCCURRED zurück, wenn sowohl DBPROP_COL_PRIMARYKEY als auch dbprop_col_unique den Wert VARIANT_TRUE haben und *DwOption* ist nicht dbpropoptions_required ist.<br /><br /> DB_E_ERRORSOCCURRED wird zurückgegeben, wenn sowohl DBPROP_COL_PRIMARYKEY als auch DBPROP_COL_UNIQUE den Wert VARIANT_TRUE haben und *dwOption* gleich DBPROPOPTIONS_REQUIRED ist. Die Spalte wird mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Identitätseigenschaft definiert, und das DBPROP_COL_PRIMARYKEY *dwStatus*-Element wird auf DBPROPSTATUS_CONFLICTING festgelegt.<br /><br /> Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt DB_S_ERRORSOCCURRED zurück, wenn sowohl DBPROP_COL_NULLABLE als auch dbprop_col_unique den Wert VARIANT_TRUE haben und *DwOption* ist nicht dbpropoptions_required ist.<br /><br /> DB_E_ERRORSOCCURRED wird zurückgegeben, wenn sowohl DBPROP_COL_NULLABLE als auch DBPROP_COL_UNIQUE den Wert VARIANT_TRUE haben und *dwOption* gleich DBPROPOPTIONS_REQUIRED ist. Die Spalte wird mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Identitätseigenschaft definiert, und das DBPROP_COL_NULLABLE *dwStatus*-Element wird auf DBPROPSTATUS_CONFLICTING festgelegt.<br /><br /> Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt einen Fehler von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Wenn der Consumer versucht, erstellen Sie eine UNIQUE-Einschränkung für eine Spalte ungültig [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp. UNIQUE-Einschränkungen können nicht für Spalten, die mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bit**-Datentyp erstellt wurden, definiert werden.|  
  
 Wenn der Consumer ruft **itabledefinition:: CreateTable**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter Tabelleneigenschaften wie folgt interpretiert.  
  
|Eigenschafts-ID|Description|  
|-----------------|-----------------|  
|DBPROP_TBL_TEMPTABLE|R/W: Lesen/Schreiben<br /><br /> Standardwert: VARIANT_FALSE Beschreibung: standardmäßig die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erstellt die Tabellen, die vom Consumer benannt. Wenn VARIANT_TRUE der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter generiert einen temporären Tabellennamen für den Consumer. Der Consumer legt den *pTableID*-Parameter von **CreateTable** auf NULL fest. Der *ppTableID*-Parameter muss einen gültigen Zeiger enthalten.|  
  
 Wenn ein Rowset geöffnet werden, auf eine erfolgreich erstellte Tabelle, fordert der Consumer die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird ein durch Cursor unterstütztes Rowset geöffnet. Alle Rowseteigenschaften können in den übergebenen Eigenschaftensätzen angegeben werden.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Tabellen und Indizes](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
