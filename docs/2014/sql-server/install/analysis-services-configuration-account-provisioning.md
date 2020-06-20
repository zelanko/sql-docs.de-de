---
title: Analysis Services Konfiguration-Konto Bereitstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services configuration
- account provisioning
ms.assetid: 169b1af2-6fe2-467f-8ca4-919f24c620ce
author: heidisteen
ms.author: heidist
ms.openlocfilehash: 109b5d9ddddf2b78c0bb8947cfa876d233f804ea
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85042709"
---
# <a name="analysis-services-configuration---account-provisioning"></a>Analysis Services-Konfiguration - Kontobereitstellung
  Verwenden Sie diese Seite zum Einrichten des Servermodus und zum Zuweisen von administrativen Berechtigungen an Benutzer oder Dienste, die uneingeschränkten Zugriff auf [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] benötigen. Während des Setups wird die lokale Windows-Gruppe „BUILTIN\Administrators“ der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Serveradministratorrolle der Instanz, die Sie installieren, nicht automatisch hinzugefügt. Wenn Sie der Serveradministratorrolle die lokale Gruppe "Administratoren" hinzufügen möchten, müssen Sie diese Gruppe explizit angeben.  
  
 Bei der Installation von [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] sollten Sie Administratoren von SharePoint-Farmen oder -Diensten, die für eine [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Serverbereitstellung in einer [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]-Farm zuständig sind, Administratorrechte gewähren. Weitere Informationen zu [!INCLUDE[ssGeminiMTS](../../includes/ssgeminimts-md.md)] den Anforderungen an die Installation und die Dienst Konten finden Sie unter [Installieren von SQL Server BI-Funktionen mit SharePoint &#40;Power Pivot und Reporting Services&#41;](../../../2014/sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md).  
  
## <a name="options"></a>Optionen  
 **Servermodus** - Der Servermodus gibt den Typ von Analysis Services-Datenbanken an, die auf dem Server bereitgestellt werden können. Servermodi werden während des Setups bestimmt und können später nicht mehr geändert werden. Die einzelnen Modi schließen einander aus. Das bedeutet, dass Sie zwei Instanzen von Analysis Services benötigen, die jeweils für einen anderen Modus konfiguriert sind, um beide klassische Lösungen - das OLAP- und das tabellarische Modell - zu unterstützen.  
  
 **Administratoren angeben** – Sie müssen mindestens einen Serveradministrator für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz angeben. Die Benutzer oder die Gruppen, die Sie angeben, werden Mitglieder der Serveradministratorrolle der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz, die Sie installieren. Diese müssen Windows-Domänenbenutzerkonten in der gleichen Domäne wie der Computer sein, auf dem Sie die Software installieren.  
  
> [!NOTE]  
>  Die Benutzerkontensteuerung (User Account Control, UAC) ist eine Windows-Sicherheitsfunktion, bei der ein Administrator administrative Aktionen oder Anwendungen einzeln genehmigen muss, bevor diese ausgeführt werden können. Da die Benutzerkontensteuerung in den Standardeinstellungen aktiviert ist, werden Sie aufgefordert, einzelne Vorgänge, für die erhöhte Berechtigungen erforderlich sind, zu genehmigen. Sie können die Benutzerkontensteuerung konfigurieren, um das Standardverhalten zu ändern, oder sie für bestimmte Programme anpassen. Weitere Informationen zur UAC-und UAC-Konfiguration finden Sie unterschritt-für- [Schritt-Anleitung zur Benutzerkontensteuerung](https://go.microsoft.com/fwlink/?linkid=196350) und [Benutzerkontensteuerung (Wikipedia)](https://go.microsoft.com/fwlink/?linkid=196351).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dienst Konten &#40;Analysis Services konfigurieren&#41;](../../../2014/analysis-services/instances/configure-service-accounts-analysis-services.md)   
 [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
  
  
