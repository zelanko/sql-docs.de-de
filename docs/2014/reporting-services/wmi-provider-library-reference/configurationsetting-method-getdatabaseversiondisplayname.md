---
title: GetDatabaseVersionDisplayName-Methode (WMI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetDatabaseVersionDisplayName method
ms.assetid: e1286424-7043-4f12-a7ad-1cf69e81baa4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05ee617f1a065c44a7c593af244d778f76a7a627
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098409"
---
# <a name="getdatabaseversiondisplayname-method-wmi"></a>GetDatabaseVersionDisplayName-Methode (WMI)
  Ruft den Anzeigenamen für eine gegebene Versionszeichenfolge in der Berichtsserver-Datenbank ab  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub GetDatabaseVersionDisplayName(Version As String, DisplayName As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetDatabaseVersionDisplayName(string Version, string DisplayName, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *Version*  
 Eine Zeichenfolge, die die Versionszeichenfolge für eine Berichtsserver-Datenbank enthält  
  
 *DisplayName*  
 [out] Eine Zeichenfolge, die den Anzeigenamen enthält, welcher der angegebenen Version entspricht  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="remarks"></a>Bemerkungen  
 In der folgenden Tabelle ist die Zuordnung der Datenbankversion zur Anzeigezeichenfolge dargestellt.  
  
|**Release**|`Version`|**Anzeige Name**|  
|-----------------|-----------------|----------------------|  
|RS 2005 SP2|
  @DBVersion = 'C.0.8.54'|SQL Server 2005 SP2|  
|RS 2005 SP1|
  @DBVersion = 'C.0.8.43'|SQL Server 2005 SP1|  
|RS 2005 RTM|
  @DBVersion = 'C.0.8.40'|SQL Server 2005|  
|RS 2000 SP2|
  @DBVersion = 'C.0.6.54'|SQL Server 2000 SP2|  
|RS 2000 SP1|
  @DBVersion = 'C.0.6.51'|SQL Server 2000 SP1|  
|RS 2000 RTM|
  @DBVersion = 'C.0.6.43'|SQL Server 2000|  
|Hotfix||Nächste geeignete Version|  
  
 Für eine *Version* vor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 wird HRESULT = ACT_E_BAD_VERSION zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
