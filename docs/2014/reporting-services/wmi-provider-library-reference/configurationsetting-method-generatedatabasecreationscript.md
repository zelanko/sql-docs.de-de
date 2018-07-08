---
title: 'GenerateDatabaseCreationScript-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
api_name:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
caps.latest.revision: 25
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 42898aba8f621688ba229fcf01d367b4da1a4f71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149031"
---
# <a name="generatedatabasecreationscript-method-wmi-msreportserverconfigurationsetting"></a>GenerateDatabaseCreationScript-Methode (WMI: MSReportServer_ConfigurationSetting)
  Generiert ein SQL-Skript, mit dem eine Berichtsserver-Datenbank erstellt werden kann  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *Databasename*  
 Eine Zeichenfolge, die den Namen der zu erstellenden Berichtsserver-Datenbank enthält  
  
 *Lcid*  
 Zur Lokalisierung von Rollennamen verwendeter Wert.  
  
 *IsSharePointMode*  
 Gibt an, ob die Datenbank im einheitlichen Modus oder im SharePoint-Modus erstellt werden soll.  
  
> [!IMPORTANT]  
>  Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], *IsSharePointMode* = `True` wird nicht unterstützt werden, da im SharePoint-Modus [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ist eine SharePoint shared Service und nicht vom WMI-Anbieter kontrolliert wird. Legen Sie diesen Parameter immer auf `False`.  
  
 *Skript*  
 [out] Eine Zeichenfolge, die das generierte SQL-Skript enthält  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode generiert ein SQL-Skript, mit dem Berichtsserver-Datenbanken für die Version des Berichtsservers erstellt werden, zu dem derzeit eine Verbindung besteht.  
  
 Der im Parameter *DatabaseName* angegebene Wert muss den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benennungskonventionen für Datenbanken entsprechen.  
  
 Die Methode überprüft beim Generieren des Skripts nicht das Vorhandensein der Datenbank.  
  
 Beim Generieren des Skripts überprüft diese Methode nicht, ob die Berichtsserver-Datenbank vorhanden ist.  
  
 Das generierte Skript unterstützt [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
