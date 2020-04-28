---
title: Mapping-Datentypen (ODBC) | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304626"
---
# <a name="mapping-data-types-odbc"></a>Zuordnen von Datentypen (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Treiber ordnet SQL-Datentypen ODBC-SQL-Datentypen zu. In den folgenden Abschnitten werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-SQL-Datentypen sowie die ODBC-SQL-Datentypen, denen sie zugeordnet werden, erläutert. Außerdem werden die ODBC-SQL-Datentypen und die zugehörigen ODBC-C-Datentypen sowie die unterstützten und standardmäßigen Konvertierungen erklärt.  
  
> [!NOTE]  
>  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Zeitstempel** -Datentyp wird dem SQL_BINARY oder SQL_VARBINARY ODBC-Datentyp zugeordnet, da die Werte in **Zeitstempel** -Spalten keine **DateTime** -Werte sind, sondern **binäre (8)** oder **varbinary (8)** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Werte, die die Sequenz der Aktivität in der Zeile angeben. Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber einen SQL_C_WCHAR-Wert (Unicode) erkennt, der eine ungerade Anzahl von Bytes enthält, wird das letzte ungerade Byte abgeschnitten.  
  
## <a name="dealing-with-sql_variant-data-type-in-odbc"></a>Arbeiten mit dem 'sql_variant'-Datentyp in ODBC  
 Die **sql_variant** -Datentyp Spalte kann beliebige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen in mit Ausnahme von großen Objekten (LOB) enthalten, z. b. **Text**, **ntext**und **Image**. Beispielsweise könnte die Spalte **smallint** -Werte für einige Zeilen, **float** -Werte für andere Zeilen und **char/nchar-** Werte im Rest enthalten.  
  
 Der **sql_variant** -Datentyp ähnelt dem **Variant** -Datentyp in Microsoft Visual Basic®.  
  
### <a name="retrieving-data-from-the-server"></a>Abrufen von Daten vom Server  
 ODBC weist kein Konzept von Variant-Typen auf, was die Verwendung des **sql_variant** -Datentyps mit einem ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Treiber in einschränkt. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in eine Bindung angegeben ist, muss der **sql_variant** Datentyp an einen der dokumentierten ODBC-Datentypen gebunden werden. **SQL_CA_SS_VARIANT_TYPE**, ein für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber spezifisches Attribut, gibt den Datentyp einer Instanz in der **sql_variant** Spalte an den Benutzer zurück.  
  
 Wenn keine Bindung angegeben wird, kann die [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) -Funktion verwendet werden, um den Datentyp einer Instanz in der **sql_variant** Spalte zu bestimmen.  
  
 Führen Sie die folgenden Schritte aus, um **sql_variant** Daten abzurufen.  
  
1.  Rufen Sie **SQLFetch** auf, um zu der abgerufenen Zeile zu positionieren.  
  
2.  Aufrufen von **SQLGetData**, angeben von SQL_C_BINARY für den-Typ und 0 für die Daten Länge. Dadurch wird der Treiber gezwungen, den **sql_variant** -Header zu lesen. Der-Header gibt den Datentyp dieser Instanz in der **sql_variant** Spalte an. **SQLGetData** gibt die Größe (in Bytes) des Werts zurück.  
  
3.  Führen Sie [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) aus, indem Sie **SQL_CA_SS_VARIANT_TYPE** als Attribut Wert angeben. Diese Funktion gibt den C-Datentyp der Instanz in der **sql_variant** Spalte an den Client zurück.  
  
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
  
 Wenn der Benutzer die Bindung mithilfe von [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)erstellt, liest der Treiber die Metadaten und die Daten. Der Treiber konvertiert die Daten dann in den entsprechenden in der Bindung angegebenen ODBC-Typ.  
  
### <a name="sending-data-to-the-server"></a>Senden von Daten an den Server  
 **SQL_SS_VARIANT**ein neuer Datentyp speziell für den Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client-ODBC-Treiber verwendet wird, wird für Daten verwendet, die an eine **sql_variant** Spalte gesendet werden. Beim Senden von Daten an den Server mit Parametern (z. b. Insert Into TableName Values (?,?)) wird [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) verwendet, um die Parameterinformationen anzugeben, einschließlich des C [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Typs und des entsprechenden Typs. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber konvertiert den C-Datentyp in einen der entsprechenden **sql_variant** Untertypen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verarbeitungsergebnisse &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
