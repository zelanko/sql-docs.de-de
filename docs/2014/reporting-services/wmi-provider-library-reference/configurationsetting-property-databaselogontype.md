---
title: 'DatabaseLogonType-Eigenschaft (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonType
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cfe28e2cf9c47f3eebaddbcaa013ad492d715748
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59941026"
---
# <a name="databaselogontype-property-wmi-msreportserverconfigurationsetting"></a>DatabaseLogonType-Eigenschaft (WMI: MSReportServer_ConfigurationSetting)
  Gibt an, ob der Berichtsserver für den Zugriff auf die Berichtsserver-Datenbank ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Dienstkonto, ein Windows-Benutzerkonto oder eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung verwendet. Schreibgeschützt.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a>Eigenschaftswerte  
 Ein `integer`-Objekt, das den Anmeldetyp darstellt  
  
## <a name="example-code"></a>Beispielcode  
 [MSReportServer_ConfigurationSetting Class (MSReportServer_ConfigurationSetting-Klasse)](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Hinweise  
 Die Werte sind:  
  
-   0 für Windows-Anmeldung  
  
-   1 für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung  
  
-   2 für Anmeldung als Dienst  
  
 Wenn 0 (Windows) angegeben wird, muss der Wert in der [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) -Eigenschaft auf ein entsprechendes gültiges Windows-Benutzerkonto festgelegt werden.  
  
 Wenn Sie 1 (SQL Server) angeben, muss der Wert von [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) einer gültigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung entsprechen.  
  
 Wenn 2 (Windows-Dienst) angegeben wird, verwendet der Berichtsserver ein [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] -Konto und das Windows-Dienstkonto für den Zugriff auf die Berichtsserver-Datenbank. Die DatabaseLogonAccount-Eigenschaft wird ignoriert.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting-Member](msreportserver-configurationsetting-members.md)  
  
  
