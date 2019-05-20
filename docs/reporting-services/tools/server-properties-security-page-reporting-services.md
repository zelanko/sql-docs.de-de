---
title: Servereigenschaften (Seite „Sicherheit“) – Reporting Services | Microsoft-Dokumentation
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.serverproperties.security.f1
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
author: maggiesMSFT
ms.author: maggies
ms.date: 06/10/2016
ms.openlocfilehash: 0e29dcf7681d105f92b3bf187c38ebe764d2449e
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65571306"
---
# <a name="server-properties-security-page---reporting-services"></a>Servereigenschaften (Seite Sicherheit) – Reporting Services

  Verwenden Sie diese [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] -Seite in [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] , um Funktionen zu deaktivieren, die potenziell einen Berichtsserver gefährden können. Die Deaktivierung dieser Features führt zu einigen Funktionseinschränkungen, kann jedoch die Gesamtsicherheit des Berichtsservers durch Verringerung bestimmter Bedrohungen erhöhen.  
  
 So öffnen Sie diese Seite
 1) Starten Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
 2) Stellen Sie eine Verbindung mit einer Berichtsserverinstanz her.
 3) Klicken Sie mit der rechten Maustaste auf den Berichtsservernamen, und wählen Sie **Eigenschaften**aus.
 4) Klicken Sie auf **Sicherheit** , um diese Seite zu öffnen.  
  
## <a name="options"></a>enthalten

### <a name="enable-windows-integrated-security-for-report-data-sources"></a>Aktivieren der integrierten Sicherheit von Windows für Berichtsdatenquellen

 Geben Sie an, ob eine Verbindung mit einer Berichtsdatenquelle mithilfe des Windows-Sicherheitstokens des Benutzers hergestellt wird, der den Bericht angefordert hat.  
  
 Wenn Sie dieses Feature deaktivieren, ist das Feature „Integrierte Sicherheit von Windows“ auf der Eigenschaftenseite der Berichtsdatenquelle nicht mehr verfügbar. Wenn Ihre Berichtsdatenquellen für die integrierte Sicherheit von Windows konfiguriert werden und Sie dann dieses Feature deaktivieren, aktualisiert der Berichtsserver sofort die Datenverbindungseigenschaften aller Ihrer Datenquellen so, dass sie Anmeldeinformationen anfordern.  
  
### <a name="enable-ad-hoc-reporting"></a>Ad-hoc-Berichterstellung aktivieren

 Geben Sie an, ob Benutzer Ad-hoc-Abfragen von einem Bericht des Berichts-Generators ausführen können, wodurch automatisch neue Berichte generiert werden, sobald ein Benutzer auf die ihn interessierenden Daten klickt.  
  
 Durch Festlegen dieser Option wird bestimmt, ob der Wert der **EnableLoadReportDefinition** -Eigenschaft auf **True** oder **False**festgelegt wird. Wenn Sie diese Option deaktivieren, wird die Eigenschaft auf **False** festgelegt, und der Berichtsserver generiert keine Berichte mit Durchklicken für Berichte, die während des Durchsuchens der Daten erstellt werden. Alle Aufrufe der **LoadReportDefinition**-Methode werden blockiert.  
  
 Die Deaktivierung dieser Option führt zu einem Sicherheitsrisiko, weil böswillige Benutzer einen Denial-of-Service-Angriff ausführen können, bei dem der Berichtsserver mit **LoadReportDefinition** -Anforderungen überlastet wird.  
  
## <a name="see-also"></a>Weitere Informationen

 [Festlegen von Berichtsservereigenschaften &#40;Management Studio&#41; ](../../reporting-services/tools/set-report-server-properties-management-studio.md) [Verbinden mit einem Berichtsserver in Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md) [Angeben von Anmelde- und Verbindungsinformationen für Berichtsdatenquellen](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md) [Berichtsserver in Management Studio: F1-Hilfe](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)
