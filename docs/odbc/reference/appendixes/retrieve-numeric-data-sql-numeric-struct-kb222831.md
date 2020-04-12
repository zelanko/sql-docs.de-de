---
title: Abrufen numerischer Daten mit SQL_NUMERIC_STRUCT | Microsoft Docs
description: C/C++ ruft mithilfe von ODBC den numerischen SQL Server-Datentyp mithilfe von SQL_NUMERIC_STRUCT ab, die sich auf SQL_C_NUMERIC beziehen.
editor: ''
ms.prod: sql
ms.technology: connectivity
ms.devlang: cpp
ms.topic: conceptual
ms.custom: ''
ms.date: 07/14/2017
ms.author: genemi
author: MightyPen
ms.openlocfilehash: ec2b68b918cbc79a245fe639108e94165be729c8
ms.sourcegitcommit: 54cfeb36c9caa51ec68fa8f4a1918e305db5e00a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219099"
---
# <a name="retrieve-numeric-data-with-sql_numeric_struct"></a>Abrufen numerischer\_Daten\_mit SQL NUMERIC STRUCT

In diesem Artikel wird beschrieben, wie numerische Daten aus dem SQL Server ODBC-Treiber in eine numerische Struktur abgerufen werden. Außerdem wird beschrieben, wie die richtigen Werte mithilfe bestimmter Genauigkeits- und Skalierungswerte angezeigt werden.

Dieser Datentyp ermöglicht es Anwendungen, numerische Daten direkt zu verarbeiten. Um das Jahr 2003 führte ODBC 3.0 einen neuen ODBC C-Datentyp ein, der von **SQL\_C\_NUMERIC**identifiziert wurde. Dieser Datentyp ist ab 2017 noch relevant.

Der verwendete C-Puffer hat die Typdefinition **von SQL\_NUMERIC\_STRUCT**. Diese Struktur enthält Felder zum Speichern der Genauigkeit, skalierung, des Vorzeichens und des Werts der numerischen Daten. Der Wert selbst wird als skalierte ganze Zahl gespeichert, wobei das am wenigsten signifikante Byte an der linken Position beginnt. 

Der Artikel [C-Datentypen](c-data-types.md) enthält weitere Informationen\_zum\_Format und zur Verwendung von SQL NUMERIC STRUCT. Im [Allgemeinen](appendix-d-data-types.md) werden in Anhang D der ODBC 3.0 Programmiererreferenz Datentypen erläutert.


## <a name="sql_numeric_struct-overview"></a>SQL\_\_NUMERIC STRUCT Übersicht


Die\_SQL\_NUMERIC STRUCT wird in der Sqltypes.h-Headerdatei wie folgt definiert:


```c
#define SQL_MAX_NUMERIC_LEN    16
typedef struct tagSQL_NUMERIC_STRUCT
{
   SQLCHAR    precision;
   SQLSCHAR   scale;
   SQLCHAR    sign;   /* 1 if positive, 0 if negative */
   SQLCHAR    val[SQL_MAX_NUMERIC_LEN];
} SQL_NUMERIC_STRUCT;
```

            
Die Genauigkeits- und Skalierungsfelder der numerischen Struktur werden nie für die Eingabe aus einer Anwendung verwendet, sondern nur für die Ausgabe vom Treiber an die Anwendung.

Der Treiber verwendet die Standardgenauigkeit (treiberdefiniert) und den Standardmaßstab (0), wenn Daten an die Anwendung zurückgegeben werden. Sofern die Anwendung keine Werte für Genauigkeit und Skalierung angibt, übernimmt der Treiber den Standardwert und kürt den Dezimalteil der numerischen Daten.

## <a name="sql_numeric_struct-code-sample"></a>SQL\_\_NUMERIC STRUCT-Codebeispiel

Dieses Codebeispiel zeigt Ihnen, wie Sie:

- Legen Sie die Genauigkeit fest.
- Legen Sie die Skala fest.
- Rufen Sie die richtigen Werte ab. 

> [!Note]
> JEDE VERWENDUNG DES IN DIESEM ARTIKEL BEREITGESTELLTEN CODES DURCH SIE ERFOLGT AUF EIGENE GEFAHR. 
>
> Microsoft stellt diese Codebeispiele "wie besehen" ohne ausdrückliche oder stillschweigende Gewährleistung zur Verfügung, einschließlich, aber nicht beschränkt auf die stillschweigenden Gewährleistungen der Marktgängigkeit und/oder Eignung für einen bestimmten Zweck.

```c
#include <stdio.h>
#include <string.h>
#include <conio.h>
#include <stdlib.h>
#include <ctype.h>
#include <windows.h>
#include <sql.h>
#include <sqlext.h>

#define MAXDSN       25
#define MAXUID       25
#define MAXAUTHSTR   25
#define MAXBUFLEN   255

SQLHENV     henv   = SQL_NULL_HENV;
SQLHDBC     hdbc1  = SQL_NULL_HDBC;     
SQLHSTMT    hstmt1 = SQL_NULL_HSTMT;
SQLHDESC    hdesc  = NULL;


SQL_NUMERIC_STRUCT NumStr;

int main()
{
   RETCODE retcode;

//Change the values below as appropriate to make a successful connection.
//szDSN: DataSourceName, szUID=userid, szAuthStr: password

UCHAR szDSN[MAXDSN+1] = "sql33",szUID[MAXUID+1]="sa", szAuthStr[MAXAUTHSTR+1] = "";
SQLINTEGER strlen1;
SQLINTEGER a;
int i,sign =1;
long myvalue, divisor;
float final_val;
   
// Allocate the Environment handle. Set the Env attribute, allocate the
//connection handle, connect to the database and allocate the statement //handle.

retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);
retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION,(SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);
retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);
retcode = SQLConnect(hdbc1, szDSN,SQL_NTS,szUID,SQL_NTS,szAuthStr,SQL_NTS);
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);

// Execute the select statement. Here it is assumed that numeric_test
//table is created using the following statements:

// Create table numeric_test (col1 numeric(5,3))
//insert into numeric_test values (25.212)

retcode = SQLExecDirect(hstmt1,(UCHAR *)"select * from numeric_test",SQL_NTS);

// Use SQLBindCol to bind the NumStr to the column that is being retrieved.

retcode = SQLBindCol(hstmt1,1,SQL_C_NUMERIC,&NumStr,19,&strlen1);

// Get the application row descriptor for the statement handle using
//SQLGetStmtAttr.

retcode = SQLGetStmtAttr(hstmt1, SQL_ATTR_APP_ROW_DESC,&hdesc, 0, NULL);

// You can either use SQLSetDescRec or SQLSetDescField when using
// SQLBindCol. However, if you prefer to call SQLGetData, you have to
// call SQLSetDescField instead of SQLSetDescRec. For more information on
// descriptors, please refer to the ODBC 3.0 Programmers reference or
// your Online documentation.

//Used when using SQLSetDescRec
//a=b=sizeof(NumStr);

// Set the datatype, precision and scale fields of the descriptor for the 
//numeric column. Otherwise the default precision (driver defined) and 
//scale (0) are returned.

// In this case, the table contains only one column, hence the second 
//parameter contains one. Zero applies to bookmark columns. Please check 
//the programmers guide for more information.

//retcode=SQLSetDescRec(hdesc,1,SQL_NUMERIC,NULL,sizeof(NumStr),5,3,&NumStr,&a,&b);

retcode = SQLSetDescField (hdesc,1,SQL_DESC_TYPE,(VOID*)SQL_C_NUMERIC,0);
retcode = SQLSetDescField (hdesc,1,SQL_DESC_PRECISION,(VOID*) 5,0);
retcode = SQLSetDescField (hdesc,1,SQL_DESC_SCALE,(VOID*) 3,0);
    
// Initialize the val array in the numeric structure.

memset(NumStr.val,0,16);
   
// Call SQLFetch to fetch the first record.

while((retcode =SQLFetch(hstmt1)) != SQL_NO_DATA)
  {
// Notice that the TargetType (3rd Parameter) is SQL_ARD_TYPE, which  
//forces the driver to use the Application Row Descriptor with the 
//specified scale and precision.

   retcode = SQLGetData(hstmt1, 1, SQL_ARD_TYPE, &NumStr, 19, &a); 

// Check for null indicator.

   if ( SQL_NULL_DATA == a )
   {
   printf( "The final value: NULL\n" );
   continue;
   }

// Call to convert the little endian mode data into numeric data.

   myvalue = strtohextoval();

// The returned value in the above code is scaled to the value specified
//in the scale field of the numeric structure. For example 25.212 would
//be returned as 25212. The scale in this case is 3 hence the integer 
//value needs to be divided by 1000.

   divisor = 1;
   if(NumStr.scale > 0)
     {
    for (i=0;i< NumStr.scale; i++)   
         divisor = divisor * 10;
     }
   final_val =  (float) myvalue /(float) divisor;

// Examine the sign value returned in the sign field for the numeric
//structure.
//NOTE: The ODBC 3.0 spec required drivers to return the sign as 
//1 for positive numbers and 2 for negative number. This was changed in the
//ODBC 3.5 spec to return 0 for negative instead of 2.

      if(!NumStr.sign) sign = -1;
      else sign  =1;

   final_val *= sign;
   printf("The final value: %f\n",final_val);
    }

   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA_FOUND);

   /* clean up */ 
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);
   SQLDisconnect(hdbc1);
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);
   SQLFreeHandle(SQL_HANDLE_ENV, henv);
   return(0);
}
```


### <a name="interim-results"></a>Zwischenergebnisse:


```console
//  C  ==> 12 * 1    =     12
//  7  ==> 07 * 16   =    112
//  2  ==> 02 * 256  =    512
//  6  ==> 06 * 4096 =  24576
===============================
                 Sum =  25212
```


In der numerischen Struktur ist das val-Feld ein Zeichenarray mit 16 Elementen. Beispielsweise wird 25.212 auf 25212 skaliert und die Skala ist 3. Im hexadezimalen Format wäre diese Zahl 627C.

Der Treiber gibt die folgenden Elemente zurück:

- Das äquivalente Zeichen von 7C, das '|' ist (Pipe) im ersten Element des Zeichenarrays.
- Das Äquivalent von 62, was im zweiten Element "b" ist.
- Die Reste der Arrayelemente enthalten Nullen, sodass der Puffer '|b'0' enthält.

Jetzt besteht die Herausforderung darin, die skalierte ganze Zahl aus diesem Zeichenfolgenarray zu erstellen. Jedes Zeichen in der Zeichenfolge entspricht zwei hexadezimalen Ziffern, d. h. der kleinsten signifikanten Ziffer (LSD) und der signifikantesten Ziffer (MSD). Der skalierte Ganzzahlwert kann generiert werden, indem jede Ziffer (LSD & MSD) mit einem Vielfachen von 16 multipliziert wird, beginnend mit 1.

Code, der die Konvertierung vom kleinen Endmodus in die skalierte Ganze ganzzahl implementiert. Es ist Ananfrage des Anwendungsentwicklers, diese Funktionalität zu implementieren. Das folgende Codebeispiel ist nur eine der vielen möglichkeiten.


```c
long strtohextoval()
{
    long val=0,value=0;
    int i=1,last=1,current;
    int a=0,b=0;

        for(i=0;i<=15;i++)
        {
         current = (int) NumStr.val[i];
         a= current % 16; //Obtain LSD
         b= current / 16; //Obtain MSD
            
         value += last* a;   
         last = last * 16;   
         value += last* b;
         last = last * 16;   
        }
     return value;
}
```


### <a name="applies-to-versions"></a>Gilt für Versionen


Die oben genannten\_\_Informationen zu SQL NUMERIC STRUCT gelten für die folgenden Produktversionen:

- Microsoft ODBC-Treiber für Microsoft SQL Server 3.7
- Microsoft Data Access Components 2.1
- Microsoft Data Access-Komponenten 2.5
- Microsoft Data Access-Komponenten 2.6
- Microsoft Data Access-Komponenten 2.7


## <a name="sql_c_numeric-overview"></a>SQL\_\_C NUMERIC-Übersicht


Das folgende Beispielprogramm veranschaulicht die\_\_Verwendung von SQL C NUMERIC, indem 123.45 in eine Tabelle eingefügt wird. In der Tabelle wird die Spalte als numerische oder Dezimalzahl mit der Genauigkeit 5 und mit dem Maßstab 2 definiert.

Der ODBC-Treiber, den Sie zum Ausführen dieses Programms verwenden, muss die ODBC 3.0-Funktionalität unterstützen.


```c
#include <windows.h>
#include <sql.h>
#include <sqlext.h>

void main() {

   SQLHENV    henv  = NULL;
   SQLHDBC    hdbc  = NULL;
   SQLHSTMT   hstmt = NULL;

   SQL_NUMERIC_STRUCT   NumStr;
   SQLINTEGER           cbNumStr = sizeof (NumStr);

   SQLAllocHandle(SQL_HANDLE_ENV, NULL, &henv);

   /* Set the ODBC behavior version. */ 
   SQLSetEnvAttr(henv,
         SQL_ATTR_ODBC_VERSION,
         (SQLPOINTER) SQL_OV_ODBC3,
         SQL_IS_INTEGER);

   SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);

   /* Substitute your own connection information */ 
   SQLConnect(hdbc,
      (SQLCHAR *) "MyDSN", 5,
      (SQLCHAR *) "UserID", 6,
      (SQLCHAR *) "Password", 8);

   SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);

   /*
      Set up the SQL_NUMERIC_STRUCT, NumStr, to hold "123.45".

      First, we need to scale 123.45 to an integer: 12345
      One way to switch the bytes is to convert 12345 to Hex:  0x3039
      Since the least significant byte will be stored starting from the
      leftmost byte, "0x3039" will be stored as "0x3930".

      The precision and scale fields are not used for input to the driver,
      only for output from the driver. The precision and scale will be set
      in the application parameter descriptor later.
   */ 

   NumStr.sign = 1;   /* 1 if positive, 2 if negative */ 

   memset (NumStr.val, 0, 16);
   NumStr.val [0] = 0x39;
   NumStr.val [1] = 0x30;

   /* SQLBindParameter needs to be called before SQLSetDescField */ 
   SQLBindParameter(hstmt,
          1,
          SQL_PARAM_INPUT,
          SQL_C_NUMERIC,
          SQL_NUMERIC,
          5,
          2,
          &NumStr,
          0,
          (SQLINTEGER *) &cbNumStr);

   /* Modify the fields in the implicit application parameter descriptor */ 
   SQLHDESC   hdesc = NULL;

   SQLGetStmtAttr(hstmt, SQL_ATTR_APP_PARAM_DESC, &hdesc, 0, NULL);
   SQLSetDescField(hdesc, 1, SQL_DESC_TYPE, (SQLPOINTER) SQL_C_NUMERIC, 0);
   SQLSetDescField(hdesc, 1, SQL_DESC_PRECISION, (SQLPOINTER) 5, 0);
   SQLSetDescField(hdesc, 1, SQL_DESC_SCALE, (SQLPOINTER) 2, 0);
   SQLSetDescField(hdesc, 1, SQL_DESC_DATA_PTR, (SQLPOINTER) &NumStr, 0);

   SQLExecDirect(hstmt,
         (SQLCHAR *) "INSERT INTO table (numeric_column) VALUES (?)",
         SQL_NTS);

   SQLFreeHandle(SQL_HANDLE_STMT, hstmt);

   SQLDisconnect (hdbc);

   SQLFreeHandle(SQL_HANDLE_DBC, hdbc);
   SQLFreeHandle(SQL_HANDLE_ENV, henv);
}
```


<!--
GeneMi historical notes, 2017/July/12. Per Jason.C

https://go.microsoft.com/fwlink/?LinkId=147596

https://support.microsoft.com/help/222831

https://web.archive.org/web/20140319133434/http:/support.microsoft.com:80/kb/222831

https://web.archive.org/web/20080505073901/http:/support.microsoft.com:80/kb/181254

https://docs.microsoft.com/sql/odbc/reference/appendixes/c-data-types
-->

