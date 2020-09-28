---
title: IBCPSession2::BCPSetBulkMode (OLE DB-Treiber) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die IBCPSession2::BCPSetBulkMode-Methode verwenden, um Massenkopien entweder aus einer Abfrage oder einer Tabelle im OLE DB-Treiber für SQL Server zu erstellen.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- BCPSetBulkMode function
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b04ede3efe3d77119a4aaadbc904f32a7c51a201
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88860207"
---
# <a name="ibcpsession2bcpsetbulkmode"></a>IBCPSession2::BCPSetBulkMode
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  IBCPSession2::BCPSetBulkMode bietet eine Alternative zu [IBCPSession::BCPColFmt &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) zum Angeben des Spaltenformats. Anders als bei IBCPSession::BCPColFmt, wo einzelne Spaltenformatattribute festgelegt werden, werden von IBCPSession2::BCPSetBulkMode alle Attribute festgelegt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
HRESULT BCPSetBulkMode (  
      int property,  
   void * pField,  
   int cbField,  
   void * pRow,  
   int cbRow  
);  
```  
  
## <a name="arguments"></a>Argumente  
 *property*  
 Eine Konstante vom Typ BYTE. Eine Liste der Konstanten finden Sie in der Tabelle im Abschnitt mit Hinweisen.  
  
 *pField*  
 Der Zeiger auf den Wert des Feldabschlusszeichens.  
  
 cbField  
 Die Länge in Bytes des Feldabschlusszeichenwerts.  
  
 pRow  
 Der Zeiger auf den Wert des Zeilenabschlusszeichens.  
  
 cbRow  
 Die Länge in Bytes des Zeilenabschlusszeichenwerts.  
  
## <a name="returns"></a>Rückgabe  
 IBCPSession2::BCPSetBulkMode kann einen der folgenden Werte zurückgeben:  
  
|||  
|-|-|  
|**S_OK**|Die Methode wurde erfolgreich ausgeführt.|  
|**E_FAIL**|Ein anbieterspezifischer Fehler ist aufgetreten. Ausführliche Informationen erhalten Sie über die ISQLServerErrorInfo-Schnittstelle.|  
|**E_UNEXPECTED**|Die Methode wurde unerwartet aufgerufen. Die **IBCPSession2::BCPInit**-Methode wurde beispielsweise erst nach dem Aufruf von IBCPSession2::BCPSetBulkMode aufgerufen.|  
|**E_INVALIDARG**|Das Argument war ungültig.|  
|**E_OUTOFMEMORY**|Fehler aufgrund von nicht genügend Arbeitsspeicher.|  
  
## <a name="remarks"></a>Bemerkungen  
 IBCPSession2::BCPSetBulkMode kann für einen Massenkopiervorgang aus einer Abfrage oder Tabelle verwendet werden. Wenn IBCPSession2::BCPSetBulkMode zum Massenkopieren aus einer Abfrageanweisung verwendet wird, muss es vor dem Aufruf von `IBCPSession::BCPControl(BCP_OPTIONS_HINTS, ...)` aufgerufen werden, um die Abfrageanweisung anzugeben.  
  
 Kombinieren Sie nicht in einem einzelnen Befehlstext die RPC-Aufrufsyntax mit der Batchabfragesyntax (z. B.`{rpc func};SELECT * from Tbl`).  Dies bewirkt, dass ICommandPrepare::Prepare einen Fehler zurückgibt, und verhindert das Abrufen von Metadaten. Verwenden Sie ODBC CALL-Syntax (z. B.`{call func}; SELECT * from Tbl`), wenn Sie die Ausführung gespeicherter Prozeduren und die Batchabfrage in einem einzelnen Befehlstext kombinieren müssen.  
  
 In der folgenden Tabelle sind die Konstanten für den *property* -Parameter aufgelistet.  
  
|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|BCP_OUT_CHARACTER_MODE|Gibt den Zeichenausgabemodus an.<br /><br /> Entspricht sowohl der Option -c in BCP.EXE als auch IBCPSession::BCPColFmt, wobei die *eUserDataType*-Eigenschaft auf **BCP_TYPE_SQLCHARACTER** festgelegt ist.|  
|BCP_OUT_WIDE_CHARACTER_MODE|Gibt den Unicode-Ausgabemodus an.<br /><br /> Entspricht sowohl der Option -w in BCP.EXE als auch IBCPSession::BCPColFmt, wobei die *eUserDataType*-Eigenschaft auf **BCP_TYPE_SQLNCHAR** festgelegt ist.|  
|BCP_OUT_NATIVE_TEXT_MODE|Gibt systemeigene Typen für Nicht-Zeichen-Typen und Unicode für Zeichentypen an.<br /><br /> Entspricht sowohl der Option -N in BCP.EXE als auch IBCPSession::BCPColFmt, wobei die *eUserDataType*-Eigenschaft auf **BCP_TYPE_SQLNCHAR** festgelegt ist, wenn der Spaltentyp eine Zeichenfolge ist, oder **BCP_TYPE_DEFAULT**, falls er keine Zeichenfolge ist.|  
|BCP_OUT_NATIVE_MODE|Gibt systemeigene Datenbanktypen an.<br /><br /> Entspricht sowohl der Option -n in BCP.EXE als auch IBCPSession::BCPColFmt, wobei die *eUserDataType*-Eigenschaft auf **BCP_TYPE_DEFAULT** festgelegt ist.|  
  
 Sie können IBCPSession::BCPControl und IBCPSession2::BCPSetBulkMode für IBCPSession::BCPControl-Optionen aufrufen, die nicht mit IBCPSession2::BCPSetBulkMode in Konflikt stehen. Beispielsweise können Sie IBCPSession::BCPControl mit **BCP_OPTION_FIRST** und IBCPSession2::BCPSetBulkMode aufrufen.  
  
 Sie können IBCPSession::BCPControl nicht mit **BCP_OPTION_TEXTFILE** und IBCPSession2::BCPSetBulkMode aufrufen.  
  
 Wenn Sie versuchen, IBCPSession2::BCPSetBulkMode mit einer Sequenz von Funktionsaufrufen aufzurufen, die IBCPSession::BCPColFmt, IBCPSession::BCPControl und IBCPSession::BCPReadFmt umfasst, gibt einer der Funktionsaufrufe einen Sequenzfehler zurück. Wenn Sie den Fehler korrigieren möchten, rufen Sie IBCPSession::BCPInit auf, um die Einstellungen zurückzusetzen und den Vorgang neu zu beginnen.  
  
 Im Folgenden werden einige Beispiele für Funktionsaufrufe dargestellt, die zu einem Funktionssequenzfehler führen:  
  
```cpp  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_IN);  
BCPSetBulkMode();  
```  
  
```cpp  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPSetBulkMode();  
BCPReadFmt();  
```  
  
```cpp  
BCPInit(NULL, "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_HINTS, "select ...");  
BCPSetBulkMode();  
```  
  
```cpp  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPSetBulkMode();  
BCPColFmt();  
```  
  
```cpp  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPReadFmt();  
BCPColFmt();  
```  
  
```cpp  
BCPInit(NULL, "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPSetBulkMode();  
BCPControl(BCP_OPTION_HINTS, "select ...");  
BCPReadFmt();  
```  
  
```cpp  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPColumns();  
```  
  
```cpp  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPSetColFmt();  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden vier Dateien mit unterschiedlichen Einstellungen von IBCPSession2::BCPSetBulkMode erstellt.  
  
```cpp  
  
// compile with: oleaut32.lib ole32.lib  
  
#include <stdio.h>  
#include "msoledbsql.h"  
  
IDBInitialize*  g_pIDBInitialize = NULL;  
IBCPSession2 * g_pIBcpSession = NULL;  
class COLEDBPropSet : public DBPROPSET {  
public:  
   COLEDBPropSet() {  
      rgProperties = NULL;  
      cProperties = 0;  
   };  
   COLEDBPropSet(const GUID& guid) {  
      rgProperties = NULL;  
      cProperties = 0;  
      guidPropertySet = guid;  
   };  
   ~COLEDBPropSet() {  
      for ( ULONG i = 0 ; i < cProperties ; i++ )  
         VariantClear(&rgProperties[i].vValue);  
      CoTaskMemFree(rgProperties);  
   }  
   void SetGUID(const GUID& guid) {  
      guidPropertySet = guid;  
   };  
   bool AddProperty(DWORD dwPropertyID, bool bValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID = dwPropertyID;  
      rgProperties[cProperties].vValue.vt = VT_BOOL;  
      rgProperties[cProperties].vValue.boolVal = (bValue) ? VARIANT_TRUE : VARIANT_FALSE;  
      cProperties++;  
      return true;  
   };  
   bool AddProperty(DWORD dwPropertyID, long nValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID  = dwPropertyID;  
      rgProperties[cProperties].vValue.vt     = VT_I4;  
      rgProperties[cProperties].vValue.lVal   = nValue;  
      cProperties++;  
      return true;  
   };  
   bool AddProperty(DWORD dwPropertyID,LPCWSTR szValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID = dwPropertyID;  
      rgProperties[cProperties].vValue.vt = VT_BSTR;  
      rgProperties[cProperties].vValue.bstrVal = SysAllocString(szValue);  
      cProperties++;  
      return true;  
   };  
   bool Add() {  
      DBPROP* p = (DBPROP*)CoTaskMemRealloc(rgProperties, (cProperties + 1) * sizeof(DBPROP));  
      if (p != NULL) {  
         rgProperties = p;  
         rgProperties[cProperties].dwOptions = DBPROPOPTIONS_REQUIRED;  
         rgProperties[cProperties].colid = DB_NULLID;  
         rgProperties[cProperties].vValue.vt = VT_EMPTY;  
         return true;  
      }  
      else  
         return false;  
   };  
};  
  
void OLEDBCleanUp() {  
   if (g_pIDBInitialize) {  
      g_pIDBInitialize->Release();  
      g_pIDBInitialize = NULL;  
   }  
   if (g_pIBcpSession) {  
      g_pIBcpSession->Release();  
      g_pIBcpSession = NULL;  
   }  
}  
  
BOOL MakeOLEDBConnect(LPWSTR  pServer) {  
   BOOL ret = true;  
   IDBProperties * pIDBProperties = NULL;  
   IDBCreateSession * pIDBCreateSession = NULL;  
   COLEDBPropSet PropSet(DBPROPSET_DBINIT);  
   COLEDBPropSet BcpProperty(DBPROPSET_SQLSERVERDATASOURCE);  
   try {  
      HRESULT hr = CoInitializeEx(NULL,COINIT_MULTITHREADED);   
      hr = CoCreateInstance(MSOLEDBSQL_CLSID, NULL, CLSCTX_INPROC_SERVER, IID_IDBInitialize, (LPVOID *)&g_pIDBInitialize);  
      if (FAILED(hr)) {  
         printf("CoCreateInstance failed\n");  
         return false;  
      }  
      PropSet.AddProperty(DBPROP_INIT_DATASOURCE, (LPWSTR)pServer);  
      PropSet.AddProperty(DBPROP_AUTH_INTEGRATED, L"SSPI");  
      hr = g_pIDBInitialize->QueryInterface(IID_IDBProperties, (void**) &pIDBProperties);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->QueryInterface(IID_IDBProperties...) failed\n");  
         throw false;  
      }  
      hr = pIDBProperties->SetProperties(1, &PropSet);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->SetProperties(...) failed\n");  
         throw false;  
      }  
      hr = g_pIDBInitialize->Initialize();  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->Initialize() failed\n");  
         throw false;  
      }  
      BcpProperty.AddProperty(SSPROP_ENABLEFASTLOAD, true);  
      BcpProperty.AddProperty(SSPROP_ENABLEBULKCOPY, true);  
      hr = pIDBProperties->SetProperties(1, &BcpProperty);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->SetProperties() for bcp failed\n");  
         throw false;  
      }  
      hr = g_pIDBInitialize->QueryInterface(IID_IDBCreateSession, (void**) &pIDBCreateSession);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->QueryInterface(IID_IDBCreateSession..) failed\n");  
         throw false;  
      }  
  
      hr = pIDBCreateSession->CreateSession(NULL, IID_IBCPSession2, (IUnknown**) &g_pIBcpSession);  
      if (FAILED(hr)) {  
         printf("g_pIDBCreateSession->CreateSession() failed\n");  
         throw false;  
      }  
   }  
   catch(...) {  
      ret = false;  
   }  
   if (pIDBProperties)  
      pIDBProperties->Release();  
   if (pIDBCreateSession)  
      pIDBCreateSession->Release();  
   return ret;  
}  
  
BOOL BCPSetBulkMode(LPWSTR pszServer, LPTSTR pszQureryOut, char BCPType, LPWSTR pszDataFile) {  
   HRESULThr;  
   if (!MakeOLEDBConnect(pszServer))  
      return false;  
   hr = g_pIBcpSession->BCPInit(NULL, pszDataFile, NULL, BCP_DIRECTION_OUT );   // bcp init for queryout  
   if (FAILED(hr)) {  
      printf("BCP init failed\n");  
      OLEDBCleanUp();  
      return false;  
   }  
   // setbulkmode  
   char ColTerm[] = "\t";  
   char RowTerm[] = "\r\n";  
   wchar_t wColTerm[] = L"\t";  
   wchar_t wRowTerm[] = L"\r\n";  
   BYTE * pColTerm = NULL;  
   int cbColTerm = NULL;  
   BYTE * pRowTerm = 0;  
   int cbRowTerm = 0;  
   int bulkmode = -1;  
  
   if(BCPType == 'c') {   // bcp -c  
      pColTerm = (BYTE*)ColTerm;  
      pRowTerm = (BYTE*)RowTerm;  
      cbColTerm = 1;  
      cbRowTerm = 2;  
      bulkmode = BCP_OUT_CHARACTER_MODE;  
   }  
   else  
      if(BCPType == 'w') {   // bcp -w  
         pColTerm = (BYTE*)wColTerm;  
         pRowTerm = (BYTE*)wRowTerm;  
         cbColTerm = 2;  
         cbRowTerm = 4;  
         bulkmode = BCP_OUT_WIDE_CHARACTER_MODE;  
      }  
      else  
         if (BCPType == 'n')   // bcp -n  
            bulkmode = BCP_OUT_NATIVE_MODE;  
         else  
            if (BCPType == 'N')   // bcp -n  
               bulkmode = BCP_OUT_NATIVE_TEXT_MODE;  
            else {  
               printf("unknown bcp mode\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            hr = g_pIBcpSession->BCPSetBulkMode(bulkmode, pColTerm, cbColTerm, pRowTerm, cbRowTerm);  
            if (FAILED(hr)) {  
               printf("BCPSetBulkMode failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
  
            // set queryout TSQL statement  
            hr = g_pIBcpSession->BCPControl(BCP_OPTION_HINTS, pszQureryOut);  
            if (FAILED(hr)) {  
               printf("BCPControl failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            // bcp copy  
            DBROWCOUNT nRowsInserted = 0;  
            hr = g_pIBcpSession->BCPExec(&nRowsInserted);  
            if (FAILED(hr)) {  
               printf("BCPExec failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            printf("bcp done\n");  
            OLEDBCleanUp();  
            return true;  
}  
  
int main() {  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -c test', 1,2") , 'c', L"bcpc.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -w test', 1,2") , 'w', L"bcpw.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -c test', 1,2") , 'n', L"bcpn.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -w test', 1,2") , 'N', L"bcp_N.dat");  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IBCPSession2 &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession2-ole-db.md)  
  
  
