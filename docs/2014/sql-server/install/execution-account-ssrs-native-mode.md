---
title: Ausführungskonto (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.executionaccount.F1
ms.assetid: 440b5a09-5fd4-4c3a-b510-f3c33cbf1c82
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e18c8c37eba48fa2732a07f4906137cdd299fdd3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312810"
---
# <a name="execution-account-ssrs-native-mode"></a>Ausführungskonto (einheitlicher SSRS-Modus)
  Verwenden Sie diese Seite, um ein Konto zu konfigurieren, das für unbeaufsichtigte Verarbeitungen verwendet werden soll. Dieses Konto wird unter bestimmten Umständen verwendet, wenn keine andere Quellen für Anmeldeinformationen verfügbar sind:  
  
-   Wenn der Berichtsserver eine Verbindung mit einer Datenquelle herstellt, für die keine Anmeldeinformationen erforderlich sind. Beispiele für Datenquellen, die möglicherweise keine Anmeldeinformationen erfordern, sind XML-Dokumente und einige clientseitige Datenbankanwendungen.  
  
-   Wenn der Berichtsserver eine Verbindung mit einem anderen Server herstellt, um externe Imagedateien oder andere Ressourcen abzurufen, auf die in einem Bericht verwiesen wird.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
 Das Festlegen dieses Kontos ist optional. Wenn es nicht festgelegt wird, werden die Verwendung externer Images und Verbindungen mit einigen Datenquellen eingeschränkt. Beim Abrufen externer Imagedateien überprüft der Berichtsserver, ob eine anonyme Verbindung hergestellt werden kann. Wenn die Verbindung kennwortgeschützt ist, verwendet der Berichtsserver das Konto für die unbeaufsichtigte Berichtsverarbeitung, um die Verbindung mit dem Remoteserver herzustellen. Wenn Daten für einen Bericht abgerufen werden, wechselt der Berichtsserver entweder die Identität des aktuellen Benutzers, fordert den Benutzer auf, Anmeldeinformationen anzugeben, verwendet gespeicherte Anmeldeinformationen oder verwendet das Konto für die unbeaufsichtigte Verarbeitung, wenn die Datenquellenverbindung **Keine** als Anmeldeinformationstyp angibt. Der Berichtsserver lässt beim Herstellen der Verbindung mit anderen Computern nicht zu, dass seine Dienstkonto-Anmeldeinformationen delegiert werden oder eine andere Identität annehmen. Daher muss das Konto für die unbeaufsichtigte Verarbeitung verwendet werden, wenn keine anderen Anmeldeinformationen verfügbar sind.  
  
 Das von Ihnen angegebene Konto darf nicht das Konto sein, das zum Ausführen des Dienstkontos verwendet wird. Wenn Sie dieses Konto konfigurieren, wird es in der Datei RSReportServer.config als verschlüsselter Wert gespeichert. Wenn Sie den Berichtsserver in einer Bereitstellung für horizontales Skalieren ausführen, müssen Sie dieses Konto auf jedem Berichtsserver auf gleiche Weise konfigurieren.  
  
 Sie können jedes beliebige Windows-Benutzerkonto verwenden. Für optimale Ergebnisse wählen Sie ein Konto aus, das über Leseberechtigungen und Netzwerkanmeldungsberechtigungen verfügt, um Verbindungen mit anderen Computern zu unterstützen. Es muss über Leseberechtigungen für ein externes Image oder eine Datendatei verfügen, das bzw. die in einem Bericht verwendet werden soll. Geben Sie nur dann ein lokales Konto ein, wenn alle Berichtsdatenquellen und externen Images auf dem Berichtsservercomputer gespeichert sind. Verwenden Sie das Konto nur für die unbeaufsichtigte Berichtsverarbeitung.  
  
> [!NOTE]  
>  Wenn Sie [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] with Advanced Services verwenden, müssen Sie dieses Konto nur konfigurieren, wenn in einem Bericht auf externe Images verwiesen wird und Berechtigungen zum Zugriff auf die Imagedateien erforderlich sind. Eine Datenquellenverbindung mit einem Remoteserver wird in SQL Server Express nicht unterstützt. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2012-Editionen unterstützte Funktionen](http://go.microsoft.com/fwlink/?linkid=232473).  
  
 Um diese Seite zu öffnen, starten die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager, und wählen **Ausführungskonto** im Navigationsbereich. Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Tastatur  
 **Ausführungskonto angeben**  
 Wählen Sie diese Option aus, um ein Konto anzugeben.  
  
 **Konto**  
 Geben Sie ein Windows-Domänenbenutzerkonto an. Verwenden Sie dieses Format: *\<Domäne>\\<Benutzerkonto\>*.  
  
 **Kennwort**  
 Geben Sie das Kennwort ein.  
  
 **Kennwort bestätigen**  
 Geben Sie das Kennwort erneut ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurations-Manager-F1-Hilfethemen &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [SSRS-Verschlüsselungsschlüssel: Speichern verschlüsselter Berichtsserverdaten](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Konfigurieren des Kontos für die unbeaufsichtigte Ausführung &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
  
  
