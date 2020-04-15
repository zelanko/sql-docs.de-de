---
title: Zuordnen von Datentypen (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [ODBC]
- result sets [ODBC], data types
- ODBC data types, mapping
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], mapping
- sql_variant data type
- SQL Server Native Client ODBC driver, data types
ms.assetid: 4ba0924d-9fca-4c48-aced-0a8d817b3dde
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 92426c854758d07a9d62ec57510d202b870dd9f2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304626"
---
# <a name="mapping-data-types-odbc"></a>Zuordnen von Datentypen (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client ODBC-Treiber ordnet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL-Datentypen ODBC SQL-Datentypen zu. In den folgenden Abschnitten werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-SQL-Datentypen sowie die ODBC-SQL-Datentypen, denen sie zugeordnet werden, erläutert. Außerdem werden die ODBC-SQL-Datentypen und die zugehörigen ODBC-C-Datentypen sowie die unterstützten und standardmäßigen Konvertierungen erklärt.  
  
> [!NOTE]  
>  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Zeitstempeldatentyp** wird dem SQL_BINARY- oder SQL_VARBINARY ODBC-Datentyp zugeordnet, da die Werte in **Timestamp-Spalten** keine **Datetime-Werte** sind, sondern **binary(8)** oder **varbinary(8)-Werte,** die die Reihenfolge der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Aktivität in der Zeile angeben. Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber einen SQL_C_WCHAR-Wert (Unicode) erkennt, der eine ungerade Anzahl von Bytes enthält, wird das letzte ungerade Byte abgeschnitten.  
  
## <a name="dealing-with-sql_variant-data-type-in-odbc"></a>Arbeiten mit dem 'sql_variant'-Datentyp in ODBC  
 Die **sql_variant** Datentypspalte kann alle Datentypen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in ausnahme große Objekte (LOBs) enthalten, z. B. **text**, **ntext**und **image**. Die Spalte kann z. B. **Smallint-Werte** für einige Zeilen, **float-Werte** für andere Zeilen und **char/nchar-Werte** im Rest enthalten.  
  
 Der **sql_variant** Datentyp ähnelt dem **Variantendatentyp** in Microsoft Visual Basic®.  
  
### <a name="retrieving-data-from-the-server"></a>Abrufen von Daten vom Server  
 ODBC verfügt nicht über ein Konzept von Variantentypen, das die Verwendung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]des **sql_variant** Datentyps mit einem ODBC-Treiber in einschränkt. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die Bindung angegeben ist, muss der **sql_variant** Datentyp an einen der dokumentierten ODBC-Datentypen gebunden sein. **SQL_CA_SS_VARIANT_TYPE**, ein neues [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Attribut, das für den ODBC-Treiber des nativen Clients spezifisch ist, gibt den Datentyp einer Instanz in der **Spalte sql_variant** an den Benutzer zurück.  
  
 Wenn keine Bindung angegeben ist, kann die [SQLGetData-Funktion](../../relational-databases/native-client-odbc-api/sqlgetdata.md) verwendet werden, um den Datentyp einer Instanz in der **Spalte sql_variant** zu bestimmen.  
  
 Führen Sie die folgenden Schritte aus, um **sql_variant** Daten abzurufen.  
  
1.  Rufen Sie **SQLFetch** auf, um die abgerufene Zeile zu positionieren.  
  
2.  Rufen Sie **SQLGetData**auf, um SQL_C_BINARY für den Typ und 0 für die Datenlänge anzugeben. Dadurch wird der Treiber dazu veranmuntert, den **header sql_variant** zu lesen. Der Header stellt den Datentyp dieser Instanz in der **Spalte sql_variant** bereit. **SQLGetData** gibt die Größe (in Bytes) des Werts zurück.  
  
3.  Rufen Sie [SQLColAttribute auf,](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) indem Sie **SQL_CA_SS_VARIANT_TYPE** als Attributwert angeben. Diese Funktion gibt den C-Datentyp der Instanz in der **Spalte sql_variant** an den Client zurück.  
  
 Im folgenden Codesegment werden die vorhergehenden Schritte gezeigt.  
  
```  
while ((retcode = SQLFetch (hstmt))==SQL_SUCCESS)  
{  
    if (retcode != SQL_SUCCESS && retcode != SQL_SUCCESS_WITH_INFO)  
    {  
        SQLError (NULL, NULL, hstmt, NULL,   
                    &lNativeError,szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    retcode = SQLGetData (hstmt, 1, SQL_C_BINARY,   
                                pBuff,0,&Indicator);//Figure out the length  
    if (retcode != SQL_SUCCESS_WITH_INFO && retcode != SQL_SUCCESS)  
    {  
        SQLError (NULL, NULL, hstmt, NULL, &lNativeError,   
                    szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    printf_s ("Byte length : %d ",Indicator); //Print out the byte length  
  
    int iValue = 0;  
    retcode = SQLColAttribute (hstmt, 1, SQL_CA_SS_VARIANT_TYPE, NULL,   
                                        NULL,NULL,&iValue);  //Figure out the type  
    printf_s ("Sub type = %d ",iValue);//Print the type, the return is C_type of the column]  
  
// Set up a new binding or do the SQLGetData on that column with   
// the appropriate type  
}  
```  
  
 Wenn der Benutzer die Bindung mit [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)erstellt, liest der Treiber die Metadaten und die Daten. Der Treiber konvertiert die Daten dann in den entsprechenden in der Bindung angegebenen ODBC-Typ.  
  
### <a name="sending-data-to-the-server"></a>Senden von Daten an den Server  
 **SQL_SS_VARIANT**, ein neuer Datentyp, der für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber spezifisch ist, wird für Daten verwendet, die an eine **sql_variant** Spalte gesendet werden. Beim Senden von Daten an den Server mithilfe von Parametern (z. B. INSERT INTO TableName VALUES (?,?)) wird [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) verwendet, um die Parameterinformationen einschließlich des C-Typs und des entsprechenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Typs anzugeben. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC-Treiber des nativen Clients konvertiert den C-Datentyp in einen der entsprechenden **sql_variant** Subtypes.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verarbeitungsergebnisse &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
