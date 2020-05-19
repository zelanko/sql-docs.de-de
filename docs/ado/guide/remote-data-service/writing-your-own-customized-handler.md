---
title: Schreiben eines eigenen benutzerdefinierten Handlers | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
- customized handler in RDS [ADO]
ms.assetid: d447712a-e123-47b5-a3a4-5d366cfe8d72
author: rothja
ms.author: jroth
ms.openlocfilehash: cd7aec0e98afd09b30c4e4d67102d1333efdcdd6
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747604"
---
# <a name="writing-your-own-customized-handler"></a>Schreiben Ihres eigenen benutzerdefinierten Handlers
Möglicherweise möchten Sie einen eigenen Handler schreiben, wenn Sie ein IIS-Server Administrator sind, der die standardmäßige RDS-Unterstützung wünscht, aber mehr Kontrolle über Benutzer Anforderungen und Zugriffsrechte hat.  
  
 Die msdfmap. Der Handler implementiert die **idatafactoriyhandler** -Schnittstelle.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="idatafactoryhandler-interface"></a>Idatafactoriyhandler-Schnittstelle  
 Diese Schnittstelle verfügt über zwei Methoden: **GetRecordSet** und **Reconnect**. Beide Methoden erfordern, dass die [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt ist.  
  
 Beide Methoden verwenden Argumente, die nach dem ersten Komma im Schlüsselwort "**Handler =**" angezeigt werden. Beispielsweise `"Handler=progid,arg1,arg2;"` übergibt eine Argument Zeichenfolge von `"arg1,arg2"` und `"Handler=progid"` übergibt ein NULL-Argument.  
  
## <a name="getrecordset-method"></a>GetRecordSet-Methode  
 Diese Methode fragt die Datenquelle ab und erstellt ein neues [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt mit den angegebenen Argumenten. Das **Recordset** muss mit **adlockbatchoptimier** geöffnet werden und darf nicht asynchron geöffnet werden.  
  
### <a name="arguments"></a>Argumente  
 ***conn***  Die Verbindungs Zeichenfolge.  
  
 ***args***  Die Argumente für den Handler.  
  
 ***Abfrage***  Der Befehls Text zum Erstellen einer Abfrage.  
  
 ***PPRS***  Der Zeiger, an dem das **Recordset** zurückgegeben werden soll.  
  
## <a name="reconnect-method"></a>Reconnect-Methode  
 Mit dieser Methode wird die Datenquelle aktualisiert. Es wird ein neues [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt erstellt und das angegebene **Recordset**angefügt.  
  
### <a name="arguments"></a>Argumente  
 ***conn***  Die Verbindungs Zeichenfolge.  
  
 ***args***  Die Argumente für den Handler.  
  
 ***pRS***  Ein **Recordset** -Objekt.  
  
## <a name="msdfhdlidl"></a>msdfhdl. idl  
 Dies ist die Schnittstellen Definition für " **idatafactor Handler** ", die in der Datei " **msdfhdl. idl** " angezeigt wird.  
  
```cpp
[  
  uuid(D80DE8B3-0001-11d1-91E6-00C04FBBBFB3),  
  version(1.0)  
]  
library MSDFHDL  
{  
    importlib("stdole32.tlb");  
    importlib("stdole2.tlb");  
  
    // TLib : Microsoft ActiveX Data Objects 2.0 Library  
    // {00000200-0000-0010-8000-00AA006D2EA4}  
    #ifdef IMPLIB  
    importlib("implib\\x86\\release\\ado\\msado15.dll");  
    #else  
    importlib("msado20.dll");  
    #endif  
  
    [  
      odl,  
      uuid(D80DE8B5-0001-11d1-91E6-00C04FBBBFB3),  
      version(1.0)  
    ]  
    interface IDataFactoryHandler : IUnknown  
    {  
HRESULT _stdcall GetRecordset(  
      [in] BSTR conn,  
      [in] BSTR args,  
      [in] BSTR query,  
      [out, retval] _Recordset **ppRS);  
  
// DataFactory will use the ActiveConnection property  
// on the Recordset after calling Reconnect.  
   HRESULT _stdcall Reconnect(  
      [in] BSTR conn,  
      [in] BSTR args,  
      [in] _Recordset *pRS);  
    };  
};  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereich für die Anpassungs Dateiverbindung](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Abschnitt "Anpassungs Datei Protokolle"](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [SQL-Abschnitt der Anpassungs Datei](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Benutzer Listen Abschnitt "Anpassungs Datei"](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Erforderliche Client Einstellungen](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Grundlegendes zur Anpassungsdatei](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)


