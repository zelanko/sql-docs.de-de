---
title: Verwenden von Datentypen mit umfangreichen Werten | Microsoft-Dokumentation
description: Verwenden von Datentypen mit umfangreichen Werten mit dem OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- large value data types
- MSOLEDBSQL, large value types
- OLE DB Driver for SQL Server, large value types
- data access [OLE DB Driver for SQL Server], large value types
- OLE DB Driver for SQL Server, large value data types
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 620ea4d2e41634f3c7da33d560affce1840fba53
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006839"
---
# <a name="using-large-value-types"></a>Verwenden von Datentypen mit umfangreichen Werten
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] war für Datentypen mit umfangreichen Werten eine besondere Behandlung erforderlich. Datentypen mit umfangreichen Werten sind solche, die die maximale Zeilengröße von 8 KB überschreiten. [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] führte einen **maximalen** Bezeichner für die Datentypen **varchar**, **nvarchar** und **varbinary** ein, um das Speichern von Werten in der Größenordnung von 2^31 -1 Byte zu ermöglichen. Tabellenspalten und [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Variablen können den Datentyp **varchar(max)** , **nvarchar(max)** oder **varbinary(max)** angeben.  
  
> [!NOTE]  
>  Datentypen mit umfangreichen Werten können eine maximale Größe zwischen 1 KB und 8 KB haben oder ohne Größenbeschränkung festgelegt werden.  
  
 Zuvor konnten nur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen wie **text**, **ntext** und **image** derartige Längen erreichen. Durch den **max**-Bezeichner für **varchar**, **nvarchar** und **varbinary** wurden diese Datentypen überflüssig. Da Datentypen mit umfangreichen Werten nach wie vor verfügbar sind, bleiben die meisten Schnittstellen zu den OLE DB-Datenzugriffskomponenten unverändert. Zu Zwecken der Abwärtskompatibilität mit vorherigen Releases wird das DBCOLUMNFLAGS_ISLONG-Kennzeichen im OLE DB-Treiber für SQL Server weiterhin verwendet. Für [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und höher entwickelte Anbieter und Treiber verwenden diese Bedingungen für die neuen Typen weiter, wenn keine Größenbeschränkung angegeben wird.  
  
> [!NOTE]  
>  Sie können die Datentypen **varchar(max)** , **nvarchar(max)** und **varbinary(max)** auch als Eingabe- und Ausgabeparametertypen für gespeicherte Prozeduren, Funktionsrückgabetypen oder in [CAST und CONVERT](../../../t-sql/functions/cast-and-convert-transact-sql.md)-Funktionen angeben.  
  
> [!NOTE]  
>  Beim Replizieren von Daten müssen Sie möglicherweise die [Serverkonfigurationsoption „Max. Textgröße für Replikation“](../../../database-engine/configure-windows/configure-the-max-text-repl-size-server-configuration-option.md) auf -1 festlegen.  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB-Treiber für SQL Server 
 Der OLE DB-Treiber für SQL Server macht die Datentypen **varchar(max)** , **varbinary(max)** und **nvarchar(max)** als DBTYPE_STR, DBTYPE_BYTES bzw. DBTYPE_WSTR verfügbar.  
  
 Spalten mit den Datentypen **varchar(max)** , **varbinary(max)** und **nvarchar(max)** , bei denen die **maximale** Größe auf „Unbegrenzt“ festgelegt ist, werden von den OLE DB-Kernschemarowsets und Schnittstellen, die Spaltendatentypen wiedergeben, als ISLONG dargestellt.  
  
 Die **IAccessor**-Implementierung des Befehlsobjekts wurde geändert, um das Binden als DBTYPE_IUNKNOWN zu ermöglichen. Wenn der Consumer DBTYPE_IUNKNOWN angibt und *pObject* auf NULL festlegt, gibt der Anbieter die **ISequentialStream**-Schnittstelle an den Consumer zurück, sodass der Consumer den **varchar(max)** -, **nvarchar(max)** - oder **varbinary(max)** -Datenstrom aus den Ausgabevariablen übertragen kann.  
  
 Aus dem Datenstrom übertragene Ausgabeparameterwerte werden nach den Ergebniszeilen zurückgegeben. Wenn die Anwendung versucht, durch Aufrufen von **IMultipleResults::GetResult** zum nächsten Resultset überzugehen, ohne alle zurückgegebenen Ausgabeparameterwerte zu verbrauchen, wird DB_E_OBJECTOPEN zurückgegeben.  
  
 Zur Unterstützung von Streaming erfordert der OLE DB-Treiber für SQL Server, dass auf Parameter mit variabler Länge in sequenzieller Reihenfolge zugegriffen wird. Dies bedeutet, dass DBPROP_ACCESSORDER entweder auf DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS oder DBPROPVAL_AO_SEQUENTIAL festgelegt werden muss, wenn die **varchar(max)** -, **nvarchchar(max)** - oder **varbinary(max)** -Spalten oder Ausgabeparameter an DBTYPE_IUNKNOWN gebunden sind. Aufrufe von **IRowset::GetData** schlagen mit DBSTATUS_E_UNAVAILABLE fehl, wenn diese Beschränkung der Zugriffsreihenfolge nicht eingehalten wird. Die Beschränkung ist nicht gültig, wenn keine Ausgabebindungen mit DBTYPE_IUNKNOWN vorhanden sind.  
  
 Der OLE DB-Treiber für SQL Server unterstützt außerdem das Binden von Ausgabeparametern als DBTYPE_IUNKNOWN für Datentypen mit umfangreichen Werten. Dies ist in Szenarios nützlich, in denen eine gespeicherte Prozedur Datentypen mit umfangreichen Werten als Rückgabewerte zurückgibt, die dem Client als DBTYPE_IUNKNOWN verfügbar gemacht werden.  
  
 Um mit diesen Typen zu arbeiten, stehen der Anwendung die folgenden Optionen zur Verfügung:  
  
-   Als Typ binden, dessen Bindungen mit dem Basistyp der Spalte unterstützt werden (z.B. Binden für nvarchar(max) als Typ, der an nvarchar gebunden werden kann). Wenn der Puffer nicht groß genug ist, werden Daten abgeschnitten, wie dies auch beim Basistyp der Fall ist, obwohl jetzt umfangreichere Werte verfügbar sind.  
  
-   Als Typ binden, dessen Konvertierungen mit dem Basistyp der Spalte unterstützt werden und der DBTYPE_BYREF angibt.  
  
-   Als DBTYPE_IUNKNOWN binden und Streaming verwenden  
  
 Beim Melden der maximalen Größe einer Spalte gibt der OLE DB-Treiber für SQL Server einen der folgenden Werte an:  
  
-   Die definierte maximale Größe, die für eine **varchar(** 2000 **)** -Spalte beispielsweise 2000 beträgt. Oder:  
  
-   Den Wert „unlimited“, der im Fall einer **varchar(max)** -Spalte ~0 entspricht. Dieser Wert wird für die DBCOLUMN_COLUMNSIZE-Metadateneigenschaft festgelegt.  
  
 Die Standardkonvertierungsregeln gelten für eine **varchar(max)** -Spalte. Dies bedeutet, dass eine Konvertierung, die für eine **varchar(** 2000 **)** -Spalte gilt, auch für eine **varchar(max)** -Spalte gültig ist. Das Gleiche gilt für **nvarchar(max)** - und **varbinary(max)** -Spalten.  
  
 Beim Abrufen von Datentypen mit umfangreichen Werten besteht der effizienteste Ansatz im Binden als DBTYPE_IUNKNOWN und Festlegen der Rowseteigenschaft DBPROP_ACCESSORDER auf DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS. Dadurch wird der Wert direkt ohne Zwischenspeichern aus dem Netzwerkdatenstrom übertragen, wie im folgenden Beispiel gezeigt:  
  
```  
#define UNICODE  
#define _UNICODE  
#define DBINITCONSTANTS  
#define INITGUID  
#define OLEDBVER 0x0250  // To include the correct interfaces.  
  
#include <stdio.h>  
#include <tchar.h>  
#include <stddef.h>  
#include <iostream>  
  
using std::cout;  
using std::endl;  
  
#include <windows.h>  
  
#include <oledb.h>  
#include "msoledbsql.h"  
#include <oledberr.h>  
  
#define CHKHR_GOTO(hr, errMsg, Label) \  
   if (FAILED(hr)) \  
   { \  
      cout << errMsg << endl; \  
      goto Label; \  
   }  
  
#define MAX_COL_SIZE 8000  
  
// ROUNDUP on all platforms pointers must be aligned properly.  
#define ROUNDUP_AMOUNT 8  
#define ROUNDUP_(size,amount) (((ULONG)(size)+((amount)-1))&~((amount)-1))  
#define ROUNDUP(size) ROUNDUP_(size, ROUNDUP_AMOUNT)  
  
HRESULT InitializeAndEstablishConnection(IDBInitialize** ppIDBInitialize);  
void UnInitializeConnection(IDBInitialize* pIDBInitialize);  
HRESULT CreateAndSetCommand(IDBInitialize* pIDBInitialize, ICommandText** ppICommandText);  
HRESULT ProcessResultSet(IRowset* pIRowset);  
  
void DisplayTime()  
{  
   SYSTEMTIME st;  
   GetSystemTime(&st);  
   cout<< st.wHour << ":" << st.wMinute << ":" << st.wSecond << "." << st.wMilliseconds << endl;  
}  
  
void main()  
{  
   HRESULT hr;  
   IDBInitialize* pIDBInitialize = NULL;  
   ICommandText* pICommandText = NULL;  
   IMultipleResults* pIMultipleResults = NULL;  
   IRowset* pIRowset = NULL;  
  
   hr = InitializeAndEstablishConnection(&pIDBInitialize);  
   CHKHR_GOTO(hr, L"Failed to establish connection.", _ExitMain);  
  
   hr = CreateAndSetCommand(pIDBInitialize, &pICommandText);  
   CHKHR_GOTO(hr, L"Failed to set up command object.", _ExitMain);  
  
   DisplayTime();  
  
   hr = pICommandText->Execute(NULL,   
      IID_IMultipleResults,   
      NULL,   
      NULL,   
     (IUnknown **) &pIMultipleResults);  
  
   CHKHR_GOTO(hr, L"Failed to execute command.", _ExitMain);  
  
   while (1)  
   {  
      hr = pIMultipleResults->GetResult(  
         NULL,   
         DBRESULTFLAG_DEFAULT,   
         IID_IRowset,   
         NULL,   
         (IUnknown**)&pIRowset);  
  
   CHKHR_GOTO(hr, L"Failed to obtain a results from MR object.", _ExitMain);  
  
   if (hr == DB_S_NORESULT)  
      break;  
  
      if (pIRowset)  
      {  
         hr = ProcessResultSet(pIRowset);   
         CHKHR_GOTO(hr, L"Failed to process the current Rowset.", _ExitMain);  
  
         pIRowset->Release();  
         pIRowset = NULL;  
      }  
   }  
  
   DisplayTime();  
  
_ExitMain:  
  
   if (pIRowset)  
   {  
      pIRowset->Release();  
      pIRowset = NULL;  
   }  
  
   if (pIMultipleResults)  
   {  
      pIMultipleResults->Release();  
      pIMultipleResults = NULL;  
   }  
  
   if (pICommandText)  
   {  
      pICommandText->Release();  
      pICommandText = NULL;  
   }  
  
   UnInitializeConnection(pIDBInitialize);  
   return;  
};  
  
HRESULT InitializeAndEstablishConnection(IDBInitialize** ppIDBInitialize)  
{  
   HRESULT hr;  
   IDBInitialize* pIDBInitialize = NULL;  
   IDBProperties* pIDBProperties = NULL;  
  
   const int NUM_DBINIT_PROPS = 3;  
   const wchar_t* const g_wszServer = L".";  
   const wchar_t* const g_wszCatalog = L"AdventureWorks";  
   const wchar_t* const g_wszSecurity = L"SSPI";  
  
   DBPROPSET rgdbPropSetInit[1];  
   DBPROP rgdbPropInit [NUM_DBINIT_PROPS];  
  
   *ppIDBInitialize = NULL;  
   hr = CoInitialize(NULL);  
   CHKHR_GOTO(hr, L"Failed to initialize COM.", _ExitInitialize);  
  
   hr = CoCreateInstance(CLSID_MSOLEDBSQL,   
      NULL,   
      CLSCTX_INPROC_SERVER,  
      IID_IDBInitialize,   
      (void**)&pIDBInitialize);  
  
   CHKHR_GOTO(hr, L"Failed to create MSOLEDBSQL DataSource object.", _ExitInitialize);  
  
   for(int idxProp = 0; idxProp < NUM_DBINIT_PROPS; idxProp++)   
   {  
      VariantInit(&rgdbPropInit[idxProp].vValue);  
   }  
  
   rgdbPropInit[0].dwPropertyID = DBPROP_INIT_DATASOURCE;  
   rgdbPropInit[0].vValue.vt = VT_BSTR;  
   rgdbPropInit[0].vValue.bstrVal= SysAllocString(g_wszServer);  
   rgdbPropInit[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgdbPropInit[0].colid = DB_NULLID;  
  
   if (rgdbPropInit[0].vValue.bstrVal == NULL)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitInitialize;  
   }  
  
   rgdbPropInit[1].dwPropertyID = DBPROP_INIT_CATALOG;  
   rgdbPropInit[1].vValue.vt = VT_BSTR;  
   rgdbPropInit[1].vValue.bstrVal= SysAllocString(g_wszCatalog);  
   rgdbPropInit[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgdbPropInit[1].colid = DB_NULLID;  
  
   if (rgdbPropInit[1].vValue.bstrVal == NULL)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitInitialize;  
   }  
  
   rgdbPropInit[2].dwPropertyID = DBPROP_AUTH_INTEGRATED;  
   rgdbPropInit[2].vValue.vt = VT_BSTR;  
   rgdbPropInit[2].vValue.bstrVal= SysAllocString(g_wszSecurity);  
   rgdbPropInit[2].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgdbPropInit[2].colid = DB_NULLID;  
  
   if (rgdbPropInit[2].vValue.bstrVal == NULL)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitInitialize;  
   }  
  
   rgdbPropSetInit[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgdbPropSetInit[0].cProperties = NUM_DBINIT_PROPS;  
   rgdbPropSetInit[0].rgProperties = rgdbPropInit;  
  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);  
   CHKHR_GOTO(hr, L"Failed to QI DataSource object for IDBProperties.", _ExitInitialize);  
  
   hr = pIDBProperties->SetProperties(1, rgdbPropSetInit);   
   CHKHR_GOTO(hr, L"Failed to set DataSource object Properties.", _ExitInitialize);  
  
   pIDBProperties->Release();  
   pIDBProperties = NULL;  
  
   hr = pIDBInitialize->Initialize();  
   CHKHR_GOTO(hr, L"Failed to establish connection with the server.", _ExitInitialize);  
  
_ExitInitialize:  
  
   if (pIDBProperties)  
   {  
      pIDBProperties->Release();  
      pIDBProperties = NULL;  
   }  
  
   if (FAILED(hr))  
   {  
      if (pIDBInitialize)  
      {  
         pIDBInitialize->Release();  
         pIDBInitialize = NULL;  
      }  
   }  
  
   *ppIDBInitialize = pIDBInitialize;  
   return hr;  
}  
  
void UnInitializeConnection(IDBInitialize* pIDBInitialize)  
{  
   if (pIDBInitialize)  
   {  
      pIDBInitialize->Uninitialize();  
      pIDBInitialize->Release();  
      pIDBInitialize = NULL;  
   }  
   CoUninitialize();  
}  
  
HRESULT CreateAndSetCommand(IDBInitialize* pIDBInitialize, ICommandText** ppICommandText)  
{  
   HRESULT hr;  
   IDBCreateSession* pIDBCreateSession = NULL;  
   IDBCreateCommand* pIDBCreateCommand = NULL;  
   ICommandText* pICommandText = NULL;  
   ICommandProperties* pICommandProperties = NULL;  
   DBPROPSET rgCmdPropSet[1];  
   DBPROP rgCmdProperties[1];  
  
const wchar_t* const g_wCmdString = L"declare @x xml, @y nvarchar(max); select @x = (SELECT * FROM Sales.SalesOrderHeader FOR XML AUTO); select @x;";  
  
   *ppICommandText = NULL;  
  
   if (!pIDBInitialize)  
   {  
      hr = E_FAIL;  
      goto _ExitCreateAndSetCommand;  
   }  
  
   hr = pIDBInitialize->QueryInterface(IID_IDBCreateSession, (void**) &pIDBCreateSession);  
   CHKHR_GOTO(hr, L"Failed to obtain IDBCreateSession interface from DSO.", _ExitCreateAndSetCommand);  
  
   hr = pIDBCreateSession->CreateSession(  
      NULL,   
      IID_IDBCreateCommand,   
      (IUnknown**) &pIDBCreateCommand);  
  
   CHKHR_GOTO(hr, L"Failed to Create a Session for command execution.", _ExitCreateAndSetCommand);  
  
   hr = pIDBCreateCommand->CreateCommand(  
      NULL,   
      IID_ICommandText,   
      (IUnknown**)&pICommandText);  
  
   CHKHR_GOTO(hr, L"Failed to Create a Command object.", _ExitCreateAndSetCommand);  
  
   hr = pICommandText->SetCommandText(DBGUID_DBSQL, g_wCmdString);  
   CHKHR_GOTO(hr, L"Failed to Set Command Text.", _ExitCreateAndSetCommand);  
  
   hr = pICommandText->QueryInterface(IID_ICommandProperties, (void**) &pICommandProperties);  
   CHKHR_GOTO(hr, L"Failed to obtain ICommandProperties interface from the command object.", _ExitCreateAndSetCommand);  
  
   rgCmdProperties[0].dwPropertyID = DBPROP_ACCESSORDER;  
   rgCmdProperties[0].vValue.vt = VT_I4;  
   rgCmdProperties[0].vValue.lVal = DBPROPVAL_AO_SEQUENTIAL;  
   rgCmdProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgCmdProperties[0].colid = DB_NULLID;  
  
   rgCmdPropSet[0].guidPropertySet = DBPROPSET_ROWSET;  
   rgCmdPropSet[0].cProperties = 1;  
   rgCmdPropSet[0].rgProperties = rgCmdProperties;  
  
   hr = pICommandProperties->SetProperties(1, rgCmdPropSet);   
   CHKHR_GOTO(hr, L"Failed to Set Command object Properties.", _ExitCreateAndSetCommand);  
  
_ExitCreateAndSetCommand:  
  
   if (pICommandProperties)  
   {  
      pICommandProperties->Release();  
      pICommandProperties = NULL;  
   }  
  
   if (pIDBCreateCommand)  
   {  
      pIDBCreateCommand->Release();  
      pIDBCreateCommand = NULL;  
   }  
  
   if (pIDBCreateSession)  
   {  
      pIDBCreateSession->Release();  
      pIDBCreateSession = NULL;  
   }  
  
   if (FAILED(hr))  
   {  
      if (pICommandText)  
      {  
         pICommandText->Release();  
         pICommandText = NULL;  
      }  
   }  
  
   *ppICommandText = pICommandText;  
   return hr;  
}  
  
HRESULT ProcessResultSet(IRowset* pIRowset)  
{  
   HRESULT hr;  
  
   IColumnsInfo* pIColumnsInfo = NULL;  
   DBCOLUMNINFO* pDBColumnInfo = NULL;  
   ULONG lNumCols = 0;  
   wchar_t* pStringsBuffer = NULL;  
  
   DBBINDING* pBindings = NULL;  
   DBOBJECT dbobj;  
   ULONG idxBinding;  
   IAccessor* pIAccessor = NULL;  
   HACCESSOR hAccessor = DB_NULL_HACCESSOR;  
   HROW hRows[1] = {DB_NULL_HROW};  
   HROW* pRow = &hRows[0];  
   BYTE* pBuffer = NULL;  
  
   ULONG lNumRowsRetrieved;  
   DBLENGTH dwOffset = 0;  
  
   hr = pIRowset->QueryInterface(IID_IColumnsInfo, (void **)&pIColumnsInfo);  
   CHKHR_GOTO(hr, L"Failed to QI Rowset for IColumnsInfo.", _ExitProcessResultSet);  
  
   hr = pIColumnsInfo->GetColumnInfo(&lNumCols, &pDBColumnInfo, &pStringsBuffer);  
   CHKHR_GOTO(hr, L"Failed to obtain Column Information.", _ExitProcessResultSet);  
  
   pBindings = new DBBINDING[lNumCols];  
  
   if (!pBindings)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitProcessResultSet;  
   }  
  
   memset(pBindings, 0, sizeof(DBBINDING) * lNumCols);  
  
   dbobj.dwFlags = STGM_READ;  
   dbobj.iid = IID_ISequentialStream;  
  
   for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)   
   {  
      pBindings[idxBinding].iOrdinal = idxBinding + 1;  
      pBindings[idxBinding].obStatus = dwOffset;  
      pBindings[idxBinding].obLength = dwOffset + sizeof(DBSTATUS);  
      pBindings[idxBinding].obValue = dwOffset + sizeof(DBSTATUS) + sizeof(DBLENGTH);  
  
      pBindings[idxBinding].pTypeInfo = NULL;  
      pBindings[idxBinding].pBindExt = NULL;  
      pBindings[idxBinding].dwPart = DBPART_VALUE | DBPART_LENGTH | DBPART_STATUS;  
      pBindings[idxBinding].dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
      pBindings[idxBinding].eParamIO = DBPARAMIO_NOTPARAM;  
      pBindings[idxBinding].bPrecision = pDBColumnInfo[idxBinding].bPrecision;  
      pBindings[idxBinding].bScale = pDBColumnInfo[idxBinding].bScale;  
  
      pBindings[idxBinding].cbMaxLen = 0;  
      pBindings[idxBinding].wType = DBTYPE_WSTR;  
  
   // Determine the maximum number of bytes required in our buffer to  
   // contain the Unicode string representation of the provider's native  
   // data type, including room for the NULL-termination character  
   switch( pDBColumnInfo[idxBinding].wType )  
   {  
      case DBTYPE_NULL:  
      case DBTYPE_EMPTY:  
      case DBTYPE_I1:  
      case DBTYPE_I2:  
      case DBTYPE_I4:  
      case DBTYPE_UI1:  
      case DBTYPE_UI2:  
      case DBTYPE_UI4:  
      case DBTYPE_R4:  
      case DBTYPE_BOOL:  
      case DBTYPE_I8:  
      case DBTYPE_UI8:  
      case DBTYPE_R8:  
      case DBTYPE_CY:  
      case DBTYPE_ERROR:  
      // When the above types are converted to a string, they  
      // will all fit into 25 characters, so use that plus space  
      // for the NULL-terminator.  
  
      pBindings[idxBinding].cbMaxLen = (25 + 1) * sizeof(WCHAR);  
      break;  
  
      case DBTYPE_DECIMAL:  
      case DBTYPE_NUMERIC:  
      case DBTYPE_DATE:  
      case DBTYPE_DBDATE:  
      case DBTYPE_DBTIMESTAMP:  
      case DBTYPE_GUID:  
      // Converted to a string, the above types will all fit into  
      // 50 characters, so use that plus space for the terminator.  
  
      pBindings[idxBinding].cbMaxLen = (50 + 1) * sizeof(WCHAR);  
      break;  
  
      case DBTYPE_BYTES:  
      // In converting DBTYPE_BYTES to a string, each byte  
      // becomes two characters (e.g. 0xFF -> "FF"), so we  
      // will use double the maximum size of the column plus  
      // include space for the NULL-terminator.  
  
      pBindings[idxBinding].cbMaxLen = (pDBColumnInfo[idxBinding].ulColumnSize * 2 + 1) * sizeof(WCHAR);  
      break;  
  
      case DBTYPE_STR:  
      case DBTYPE_WSTR:  
      case DBTYPE_BSTR:  
      // Going from a string to our string representation,  
      // we can just take the maximum size of the column,  
      // a count of characters, and include space for the  
      // terminator, which is not included in the column size.  
  
      pBindings[idxBinding].cbMaxLen = (pDBColumnInfo[idxBinding].ulColumnSize + 1) * sizeof(WCHAR);  
      break;  
  
      default:  
      // For any other type, we will simply use our maximum  
      // column buffer size, since the display size of these  
      // columns may be variable (e.g. DBTYPE_VARIANT) or  
      // unknown (e.g. provider-specific types).  
      pBindings[idxBinding].cbMaxLen = MAX_COL_SIZE;  
      break;  
   }  
  
   // If the provider's native data type for this column is  
   // DBTYPE_IUNKNOWN or this is a BLOB column and the user  
   // has requested that we bind BLOB columns as ISequentialStream  
   // objects, bind this column as an ISequentialStream object if  
   // the provider supports our creating another ISequentialStream  
   // binding.  
   if(pDBColumnInfo[idxBinding].dwFlags & DBCOLUMNFLAGS_ISLONG)  
   {  
      pBindings[idxBinding].wType = DBTYPE_IUNKNOWN;  
  
      pBindings[idxBinding].cbMaxLen = sizeof(ISequentialStream*);  
  
      pBindings[idxBinding].pObject = (DBOBJECT *)CoTaskMemAlloc(sizeof(DBOBJECT));  
  
      if (!pBindings[idxBinding].pObject)  
      {  
         hr = E_OUTOFMEMORY;  
         goto _ExitProcessResultSet;  
      }  
  
      // Direct the provider to create an ISequentialStream  
      // object over the data for this column.  
      pBindings[idxBinding].pObject->iid = IID_ISequentialStream;  
  
      // We want read access on the ISequentialStream  
      // object that the provider will create for us  
      pBindings[idxBinding].pObject->dwFlags = STGM_READ;  
      }  
  
      // Ensure that the bound maximum length is no more than the  
      // maximum column size in bytes that we've defined.  
      pBindings[idxBinding].cbMaxLen = min(pBindings[idxBinding].cbMaxLen, MAX_COL_SIZE);  
  
      // Update the offset past the end of this column's data, so  
      // that the next column will begin in the correct place in  
      // the buffer.  
      dwOffset = pBindings[idxBinding].cbMaxLen + pBindings[idxBinding].obValue;  
  
      // Ensure that the data for the next column will be correctly  
      // aligned for all platforms, or, if we're done with columns,  
      // that if we allocate space for multiple rows that the data  
      // for every row is correctly aligned.  
      dwOffset = ROUNDUP(dwOffset);  
   }  
  
   hr = pIRowset->QueryInterface(IID_IAccessor, (void **) &pIAccessor);  
   CHKHR_GOTO(hr, L"Failed to obtain Accessor interface", _ExitProcessResultSet);  
  
   hr = pIAccessor->CreateAccessor(DBACCESSOR_ROWDATA,  
      lNumCols,  
      pBindings,  
      0,  
      &hAccessor,  
      NULL);  
  
   CHKHR_GOTO(hr, L"Failed to create Accessor", _ExitProcessResultSet);  
   for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)   
   {  
      cout << pDBColumnInfo[idxBinding].pwszName << endl;  
   }  
  
   lNumRowsRetrieved = 0;  
  
   hr = pIRowset->GetNextRows(  
      NULL,  
      0,  
      1,  
      &lNumRowsRetrieved,  
      &pRow);  
  
   CHKHR_GOTO(hr, L"Failed to fetch a row from the rowset", _ExitProcessResultSet);  
  
   pBuffer = new BYTE[sizeof(DBSTATUS) + sizeof(DBLENGTH) + sizeof(IUnknown*)];  
  
   if (!pBuffer)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitProcessResultSet;  
   }  
  
   while(lNumRowsRetrieved && hr != DB_S_ENDOFROWSET)   
   {  
      memset(pBuffer, 0, sizeof(DBSTATUS) + sizeof(DBLENGTH) + sizeof(IUnknown*));  
  
      hr = pIRowset->GetData(hRows[0], hAccessor, pBuffer);  
      CHKHR_GOTO(hr, L"Failed to obtain row data", _ExitProcessResultSet);  
  
      for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)  
      {  
         if (pBindings[idxBinding].wType == DBTYPE_IUNKNOWN)  
         {  
            BYTE pbBuff[3000];  
            ULONG cbNeeded = sizeof(pbBuff)/sizeof(BYTE);  
            ULONG cbRead;  
            ULONG cbReadTotal = 0;  
            ISequentialStream* pISequentialStream = NULL;  
  
            IUnknown* pIUnknown = *((IUnknown**)(pBuffer + pBindings[idxBinding].obValue));  
            pIUnknown->QueryInterface(IID_ISequentialStream, (void**)&pISequentialStream);  
  
            do  
            {  
               hr = pISequentialStream->Read(pbBuff, cbNeeded, &cbRead);  
               cbReadTotal += cbRead;  
            }  
            while (SUCCEEDED(hr) && hr != S_FALSE && cbRead == cbNeeded);  
  
               cout << "Total Bytes Read: " << cbReadTotal << endl;  
  
               pISequentialStream->Release();  
               pISequentialStream = NULL;  
               pIUnknown->Release();  
               pIUnknown = NULL;  
            }  
         }  
  
         pIRowset->ReleaseRows(1, pRow, NULL, NULL, NULL);  
  
         hr = pIRowset->GetNextRows(NULL,  
            0,  
            1,  
            &lNumRowsRetrieved,  
            &pRow);  
  
         CHKHR_GOTO(hr, L"Failed to fetch a row from the rowset.", _ExitProcessResultSet);  
   }  
  
_ExitProcessResultSet:  
  
   pIRowset->ReleaseRows(1, pRow, NULL, NULL, NULL);  
   delete [] pBuffer;  
  
   if (pIAccessor)  
   {  
      if (hAccessor != DB_NULL_HACCESSOR)  
      {  
         pIAccessor->ReleaseAccessor(hAccessor, NULL);  
      }  
  
      pIAccessor->Release();  
      pIAccessor = NULL;  
   }  
  
   if (pBindings)  
   {  
      for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)  
      {  
         if (pBindings[idxBinding].pObject)  
         CoTaskMemFree(pBindings[idxBinding].pObject);  
      }  
   }  
  
   delete [] pBindings;  
  
   CoTaskMemFree(pDBColumnInfo);  
   CoTaskMemFree(pStringsBuffer);  
  
   if (pIColumnsInfo)  
   {  
      pIColumnsInfo->Release();  
      pIColumnsInfo = NULL;  
   }  
  
   return hr;  
}  
```  
  
 Weitere Informationen dazu, wie der OLE DB-Treiber für SQL Server Datentypen mit umfangreichen Werten verfügbar macht, finden Sie unter [Blobs und OLE-Objekte](../../oledb/ole-db-blobs/blobs-and-ole-objects.md).  

  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
