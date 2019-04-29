---
title: Schreiben Ihres eigenen benutzerdefinierten Handlers | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: daddb9057775e1f098754dd2a331c1dc77194d10
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63155911"
---
# <a name="writing-your-own-customized-handler"></a>Schreiben Ihres eigenen benutzerdefinierten Handlers
Sie möchten Ihre eigenen Handler schreiben, wenn Sie einen IIS-Server-Administrator, möchte die standardmäßige RDS zu unterstützen sind, aber mehr Kontrolle über die benutzeranforderungen und Zugriffsrechte.  
  
 Durch den MSDFMAP. Handler implementiert die **IDataFactoryHandler** Schnittstelle.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="idatafactoryhandler-interface"></a>IDataFactoryHandler-Schnittstelle  
 Diese Schnittstelle verfügt über zwei Methoden, **GetRecordset** und **Reconnect**. Beide Methoden erfordern, die die [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaft festgelegt werden, um **AdUseClient**.  
  
 Beide Methoden verwenden Argumente, die nach dem ersten Komma in angezeigt werden. die "**Handler =**" Schlüsselwort. Z. B. `"Handler=progid,arg1,arg2;"` übergibt Argumentzeichenfolge `"arg1,arg2"`, und `"Handler=progid"` wird ein null-Argument übergeben.  
  
## <a name="getrecordset-method"></a>GetRecordset-Methode  
 Diese Methode fragt die Datenquelle und erstellt ein neues [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt mit den angegebenen Argumenten. Die **Recordset** muss geöffnet sein, mit **AdLockBatchOptimistic** und müssen nicht asynchron geöffnet werden.  
  
### <a name="arguments"></a>Argumente  
 ***Conn*** der Verbindungszeichenfolge angegeben.  
  
 ***Args*** die Argumente für den Ereignishandler.  
  
 ***Abfrage*** der Befehlstext für eine Abfrage.  
  
 ***PpRS*** den Zeiger, in denen die **Recordset** zurückgegeben werden sollen.  
  
## <a name="reconnect-method"></a>Reconnect-Methode  
 Diese Methode aktualisiert die Datenquelle. Er erstellt ein neues [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) -Objekt und fügt die angegebene **Recordset**.  
  
### <a name="arguments"></a>Argumente  
 ***Conn*** der Verbindungszeichenfolge angegeben.  
  
 ***Args*** die Argumente für den Ereignishandler.  
  
 ***pRS*** ein **Recordset** Objekt.  
  
## <a name="msdfhdlidl"></a>msdfhdl.idl  
 Dies ist die Schnittstellendefinition für **IDataFactoryHandler** , angezeigt wird, der **///msdfhdl.idl** Datei.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Connect-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Logs-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [SQL-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [UserList-Abschnitt der Anpassungsdatei](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Erforderliche Clienteinstellungen](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Grundlegendes zu der Anpassungsdatei](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)


