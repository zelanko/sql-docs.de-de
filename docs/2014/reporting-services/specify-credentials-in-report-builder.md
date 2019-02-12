---
title: Angeben von Anmeldeinformationen im Berichts-Generator | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 7412ce68-aece-41c0-8c37-76a0e54b6b53
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: 6fff4c4110f6f51c8e2363cff1fb64633caeb888
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56024301"
---
# <a name="specify-credentials-in-report-builder"></a>Angeben von Anmeldeinformationen im Berichts-Generator
  Anmeldeinformationen authentifizieren den Benutzer, der Daten von einer Datenquelle abrufen möchte. Der Besitzer der Datenquelle legt den Typ der Anmeldeinformationen fest, die verwendet werden müssen. Ein Datenbankadministrator kann zum Beispiel festlegen, dass der Benutzer einen Windows-Benutzernamen und ein Kennwort angeben muss.  
  
 In einer Berichtsdefinition legt jede Datenquellendefinition einen Namen und eine Verbindungszeichenfolge fest, ob integrierte Sicherheit zu verwenden ist und welche Aufforderung anzuzeigen ist, wenn Anmeldeinformationen erforderlich sind, jedoch nicht angegeben wurden. Anmeldeinformationen werden nicht in der Berichtsdefinition gespeichert. Nach Veröffentlichen eines Berichts auf dem Berichtserver können Datenquellen unabhängig von einer Berichtsdefinition verwaltet werden. Datenquellenbesitzer können auf dem Berichtsserver Anmeldeinformationen für eingebettete und freigegebene Datenquellen festlegen.  
  
> [!NOTE]  
>  Der Berichtsserveradministrator muss einem Benutzer die entsprechenden Berechtigungen zum Durchsuchen des Berichtsservers gewähren, um freigegebene Datenquellen oder Modelle auszuwählen oder Berichte zu öffnen oder zu speichern. Weitere Informationen finden Sie unter [Installation, Deinstallation und Unterstützung von Berichts-Generator](../../2014/reporting-services/install-uninstall-and-report-builder-support.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
## <a name="understanding-when-credentials-are-used"></a>Grundlegendes zur Verwendung von Anmeldeinformationen  
 Im Berichts-Generator werden Anmeldeinformationen häufig zum Herstellen einer Verbindung mit einem Berichtsserver oder für datenbezogene Aufgaben verwendet – beispielsweise für das Erstellen einer eingebetteten Datenquelle, das Ausführen einer Datasetabfrage oder das Anzeigen der Vorschau eines Berichts. Anmeldeinformationen werden nicht im Bericht gespeichert. Sie werden getrennt auf dem Berichtsserver oder dem lokalen Client verwaltet. In der folgenden Liste werden die Anmeldeinformationstypen, die Sie möglicherweise angeben müssen, sowie deren Speicherort und deren Verwendung beschrieben:  
  
-   Die Berichtsserver-Anmeldeinformationen, die Sie im Dialogfeld [Reporting Services-Anmeldung (Dialogfeld) (Berichts-Generator)](report-builder/reporting-services-login-dialog-box-report-builder.md) eingeben.  
  
     Beim erstmaligen Speichern, Veröffentlichen oder Navigieren auf einem Berichtsserver oder einer SharePoint-Website müssen unter Umständen Anmeldeinformationen angegeben werden. Die eingegebenen Anmeldeinformationen werden bis zum Ende der Berichts-Generator-Sitzung verwendet. Wenn Sie sich zum Speichern der Anmeldeinformationen entschließen, werden diese zusammen mit den Benutzereinstellungen sicher auf dem Computer gespeichert. In nachfolgenden Berichts-Generator-Sitzungen werden gespeicherte Anmeldeinformationen verwendet, um eine Verbindung mit dem gleichen Berichtsserver oder der gleichen SharePoint-Website herzustellen. Der Berichtsserveradministrator oder SharePoint-Administrator legt fest, welcher Anmeldeinformationstyp verwendet wird.  
  
-   Anmeldeinformationen für die Datenquelle, die Sie auf der Seite [Datenquellen-Anmeldeinformationen eingeben (Dialogfeld), (Berichts-Generator)](../../2014/reporting-services/data-source-properties-dialog-box-credentials-report-builder.md) für eine eingebettete Datenquelle eingeben.  
  
     Diese Anmeldeinformationen werden vom Berichtsserver verwendet, um eine Datenverbindung mit der externen Datenquelle herzustellen. Für einige Datenquellentypen können Anmeldeinformationen auf dem Berichtsserver sicher gespeichert werden. Dank dieser Anmeldeinformationen können andere Benutzer den Bericht ausführen, ohne Anmeldeinformationen für die zugrunde liegende Datenverbindung angeben zu müssen.  
  
-   Anmeldeinformationen für die Datenquelle, die Sie im Dialogfeld [Datenquellen-Anmeldeinformationen eingeben (Dialogfeld), (Berichts-Generator)](report-data/enter-data-source-credentials-dialog-box-report-builder.md) eingeben, wenn Sie eine Datasetabfrage ausführen, Datasetfelder aktualisieren oder eine Vorschau des Berichts anzeigen.  
  
     Diese Anmeldeinformationen werden verwendet, um eine Datenverbindung zwischen Berichts-Generator und externer Datenquelle herzustellen oder die Vorschau eines Berichts anzuzeigen, der zum Anfordern von Anmeldeinformationen konfiguriert ist. Anmeldeinformationen, die Sie in diesem Dialogfeld eingeben, werden nicht auf dem Berichtsserver gespeichert und können nicht von anderen Benutzern verwendet werden. Die Anmeldeinformationen werden während der Bearbeitungssitzung von Berichts-Generator für den Bericht zwischengespeichert, damit sie nicht bei jeder Ausführung der Abfrage und bei jeder Anzeige der Berichtsvorschau erneut eingegeben werden müssen.  
  
     Verwenden Sie für freigegebene Datenquellen die Option **Kennwort speichern** , um die Anmeldeinformationen zusammen mit den Benutzereinstellungen lokal auf dem Computer zu speichern. Die gespeicherten Anmeldeinformationen werden vom Berichts-Generator bei jeder Verbindungsherstellung mit der entsprechenden externen Datenquelle verwendet.  
  
 Weitere Informationen finden Sie unter [Datenquelleneigenschaften, Dialogfeld „Allgemein“ (Berichts-Generator)](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md) und [Anzeigen einer Berichtsvorschau in Berichts-Generator](report-builder/previewing-reports-in-report-builder.md).  
  
## <a name="types-of-credentials"></a>Anmeldeinformationstypen  
 Der Besitzer der Datenquelle legt den Typ der Anmeldeinformationen fest, die eine Datenquelle unterstützt. Um z. B. auf eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank zuzugreifen, müssen Sie möglicherweise einen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anmeldebenutzernamen und ein Kennwort angeben. Um auf eine andere Datenquelle zuzugreifen, müssen Sie möglicherweise einen Windows-Benutzernamen und ein Kennwort angeben. Für einige Datenquellen sind eventuell keine Anmeldeinformationen erforderlich.  
  
### <a name="options-for-specifying-credentials"></a>Optionen für die Angabe von Anmeldeinformationen  
 Die folgenden Optionen sind für die Angabe von Anmeldeinformationen für eine Datenquelle verfügbar:  
  
-   Verwendung des aktuellen Windows-Benutzers (auch bekannt als integrierte Sicherheit).  
  
-   Verwendung eines gespeicherten Benutzernamens und eines gespeicherten Kennworts.  
  
-   Aufforderung zur Eingabe der Anmeldeinformationen durch den Benutzer  
  
-   Anmeldeinformationen sind nicht erforderlich.  
  
### <a name="windows-integrated-security"></a>Integrierte Sicherheit von Windows  
 Wenn Sie **Windows-Authentifizierung verwenden (integrierte Sicherheit)** auswählen, wird das Sicherheitstoken des aktuellen Benutzers an die Datenquelle übergeben. In diesem Fall wird der Benutzer nicht aufgefordert, einen Benutzernamen oder ein Kennwort einzugeben. Diese Option erfordert normalerweise die Aktivierung von Delegierungsfunktionen. Wenn diese funktionen nicht aktiviert sind, können Sie diese Option nur verwenden, um auf eine Datenquelle zuzugreifen, die sich auf demselben Computer befindet.  
  
### <a name="user-name-and-password-login"></a>Anmeldung mit Benutzername und Kennwort  
 Wenn Sie **Diesen Benutzernamen und dieses Kennwort verwenden**auswählen, müssen Benutzername und Kennwort für den Zugriff auf die Datenquelle angegeben werden. Bei einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank sind dies möglicherweise die Anmeldeinformationen für eine Datenbankanmeldung. Die Anmeldeinformationen werden zur Authentifizierung an die Datenquelle übergeben.  
  
### <a name="prompted-credentials"></a>Aufforderung zur Eingabe der Anmeldeinformationen  
 Wenn Sie eine Aufforderung zur Eingabe von Anmeldeinformationen angeben, muss jeder Benutzer, der auf den Bericht zugreift, einen Benutzernamen und ein Kennwort zum Abrufen der Daten eingeben. Diese Option wird für Berichte mit vertraulichen Daten empfohlen. Bei den angeforderten Anmeldeinformationen kann es sich um die Anmeldeinformationen für ein Windows-Konto oder für eine Datenbank-Anmeldung handeln. Wenn der Datenbankserver die angegebenen Anmeldeinformationen nicht erkennt oder wenn dem angegebenen Benutzer keine Berechtigung zum Abrufen der Daten gewährt wurde, kann die Verbindung nicht hergestellt werden.  
  
### <a name="no-credentials"></a>Keine Anmeldeinformationen  
 Für diese Datenquelle sind keine Anmeldeinformationen erforderlich. Um diesen Bericht auf dem Berichtsserver auszuführen, muss das Konto für die unbeaufsichtigte Ausführung konfiguriert werden. Weitere Informationen finden Sie unter [Konfigurieren des unbeaufsichtigten Ausführungskontos &#40;SSRS-Konfigurations-Manager&#41; ](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Dokumentation in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren und Deinstallieren von Berichts-Generator-Unterstützung](../../2014/reporting-services/install-uninstall-and-report-builder-support.md)   
 [Eingebettete und freigegebene Datenverbindungen oder Datenquellen &#40;Berichts-Generator und SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [Berichts-Generator-Optionen im Dialogfeld Einstellungen &#40;Berichts-Generator&#41;](report-builder/set-default-options-for-report-builder.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)   
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Hinzufügen und Prüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
  
