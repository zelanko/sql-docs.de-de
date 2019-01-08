---
title: Aktualisieren von Berichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], upgrading
- published reports [Reporting Services], upgrades
- custom report items, upgrading
- Reporting Services, upgrades
- upgrading Reporting Services
- snapshots [Reporting Services], upgrading
- report definition files [Reporting Services]
- .rdl files
ms.assetid: a1a10c67-7462-4562-9b07-a8822188a161
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2b80d5a5fcdc5b95b7d82ce1e5f5deebd4de5f7d
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52538345"
---
# <a name="upgrade-reports"></a>Upgrade Reports
  Berichtsdefinitionsdateien (RDL) werden auf folgende Weise automatisch aktualisiert:  
  
-   Wenn Sie einen Bericht im Berichts-Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]öffnen, wird die Berichtsdefinition auf das derzeit unterstützte RDL-Schema aktualisiert. Wenn Sie in den Projekteigenschaften einen [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] - oder einen [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] -Berichtsserver angeben, wird die Berichtsdefinition in einem Schema gespeichert, das mit dem Zielserver kompatibel ist.  
  
-   Wenn Sie eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation auf eine [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Installation aktualisieren, werden vorhandene Berichte und Momentaufnahmen, die auf einem Berichtsserver veröffentlicht wurden, kompiliert und automatisch auf das neue Schema aktualisiert, wenn sie zum ersten Mal verarbeitet werden. Wenn ein Bericht nicht automatisch aktualisiert werden kann, wird er im Abwärtskompatibilitätsmodus verarbeitet. Die Berichtsdefinition bleibt im ursprünglichen Schema erhalten.  
  
 Berichte werden nicht aktualisiert, wenn Sie eine Berichtsdefinitionsdatei direkt auf den Berichtsserver oder auf eine SharePoint-Website hochladen. Das Upgrade einer Berichtsdefinition in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] ist die einzige Möglichkeit, die RDL-Datei zu aktualisieren.  
  
 Nachdem ein Bericht lokal oder auf dem Berichtsserver aktualisiert wurde, werden möglicherweise weitere Fehler, Warnungen und Meldungen angezeigt. Das ist das Ergebnis der Änderungen am internen Berichtsobjektmodell und an Verarbeitungskomponenten, die das Anzeigen von Meldungen bewirken, sobald zugrunde liegende Probleme im Bericht erkannt werden. Weitere Informationen finden Sie unter [Reporting Services Backward Compatibility](../reporting-services-backward-compatibility.md).  
  
 Weitere Informationen zu neuen Funktionen für [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)], finden Sie unter [neues &#40;Reporting Services&#41;](../what-s-new-reporting-services.md).  
  
 In diesem Thema:  
  
-   [Vom Upgrade unterstützte Versionen](#bkmk_versionsupported)  
  
-   [Berichtsdefinitionsdateien (RDL-Dateien) und Berichts-Designer](#bkmk_rdlfiles)  
  
-   [Veröffentlichte Berichte und Berichtsmomentaufnahmen](#bkmk_publishedreports_and_snapshots)  
  
-   [Abwärtskompatibilitätsmodus](#bkmk_backcompat)  
  
-   [Aktualisieren eines Berichts mit Unterberichten](#bkmk_subreports)  
  
-   [Aktualisieren eines Berichts mit benutzerdefinierten Berichtselementen](#bkmk_CRIs)  
  
-   [CRI konvertieren (Dialogfeld)](#bkmk_convertCRIdialog)  
  
##  <a name="bkmk_versionsupported"></a> Vom Upgrade unterstützte Versionen  
 Berichte, die in einer vorherigen Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erstellt wurden, können aktualisiert werden. Dazu gehören die folgenden Versionen:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 mit Service Pack 1  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 mit Service Pack 2  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
##  <a name="bkmk_rdlfiles"></a> Berichtsdefinitionsdateien (RDL-Dateien) und Berichts-Designer  
 Eine Berichtsdefinitionsdatei schließt einen Verweis auf den RDL-Namespace ein, der die Version des Berichtsdefinitionsschemas angibt, das zur Überprüfung der RDL-Datei verwendet wird.  
  
 Wenn Sie eine RDL-Datei im Berichts-Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]öffnen und der Bericht für einen vorherigen Namespace erstellt wurde, erstellt der Berichts-Designer automatisch eine Sicherungsdatei und aktualisiert den Bericht auf den aktuellen Namespace. Dies ist die einzige Möglichkeit, wie Sie eine Berichtsdefinitionsdatei aktualisieren können.  
  
 Die von Ihnen festgelegten Bereitstellungseigenschaften können das Schema beeinflussen, in dem die Berichtsdefinitionsdatei gespeichert wird. Weitere Informationen finden Sie unter [Bereitstellung und Versionsunterstützung in SQL Server Data Tools &#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).  
  
 Sie können eine mit einer früheren Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erstellte RDL-Datei auf einen [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Berichtsserver hochladen. Die Datei wird automatisch aktualisiert, wenn sie zum ersten Mal verwendet wird. Der Berichtsserver speichert die Berichtsdefinitionsdatei im ursprünglichen Format. Der Bericht wird automatisch aktualisiert, wenn er zum ersten Mal angezeigt wird. Die gespeicherte Berichtsdefinitionsdatei wird jedoch nicht verändert.  
  
> [!NOTE]  
>  Sie können einen Bericht, der über den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Berichtsdefinitionsnamespace verfügt, nicht auf einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005-Berichtsserver hochladen oder dort veröffentlichen.  
  
 Informationen zum Ermitteln des aktuellen RDL-Schemas für einen Bericht, einen Berichtsserver oder den Berichts-Designer finden Sie unter [Suchen der Berichtsdefinitions-Schemaversion &#40;SSRS&#41;](../reports/find-the-report-definition-schema-version-ssrs.md).  
  
##  <a name="bkmk_publishedreports_and_snapshots"></a> Veröffentlichte Berichte und Berichtsmomentaufnahmen  
 Bei der ersten Verwendung versucht der Berichtsserver, vorhandene veröffentlichte Berichte und Berichtsmomentaufnahmen auf das neue Berichtsdefinitionsschema zu aktualisieren, ohne dass Sie etwas unternehmen müssen. Es wird versucht, das Upgrade auszuführen, wenn der Benutzer einen Bericht oder eine Berichtsmomentaufnahme anzeigt bzw. wenn der Berichtsserver ein Abonnement verarbeitet. Die Berichtsdefinition wird nicht ersetzt, sondern weiterhin auf dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Berichtsserver im ursprünglichen Schema gespeichert. Wenn ein Bericht nicht automatisch aktualisiert werden kann, wird er im Abwärtskompatibilitätsmodus ausgeführt.  
  
##  <a name="bkmk_backcompat"></a> Abwärtskompatibilitätsmodus  
 Berichte, die erfolgreich aktualisiert wurden, werden vom [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Berichtsprozessor verarbeitet. Wenn ein Bericht nicht automatisch aktualisiert werden kann, wird er vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsprozessor im Abwärtskompatibilitätsmodus verarbeitet. Ein Bericht kann nicht von beiden Berichtsprozessoren verarbeitet werden. Bei der ersten Verwendung wird ein Bericht entweder erfolgreich aktualisiert oder für den Abwärtskompatibilitätsmodus markiert.  
  
 Nur der [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Berichtsprozessor unterstützt neue Funktionen. Wenn ein Bericht nicht aktualisiert werden kann, können Sie zwar den gerenderten Bericht anzeigen, die neuen Funktionen sind jedoch nicht verfügbar. Um die neuen Funktionen nutzen zu können, muss ein Bericht erfolgreich aktualisiert werden.  
  
##  <a name="bkmk_subreports"></a> Aktualisieren eines Berichts mit Unterberichten  
 Wenn ein Bericht Unterberichte enthält, kann einer von vier möglichen Zustände während des Upgrades auftreten:  
  
-   Der Hauptbericht und alle Unterberichte können erfolgreich aktualisiert werden. Sie werden vom [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Berichtsprozessor verarbeitet.  
  
-   Der Hauptbericht und alle Unterberichte können nicht aktualisiert werden. Sie werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsprozessor verarbeitet.  
  
-   Der Hauptbericht kann aktualisiert werden, aber ein oder mehrere Unterberichte können nicht aktualisiert werden. Der Hauptbericht wird vom verarbeitet die [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] Berichtsprozessor, aber im gerenderten Bericht wird die Meldung "Fehler: Unterbericht konnte nicht in den Speicherort, in dem der Unterbericht konnte nicht aktualisiert werden angezeigt, würde, verarbeitet werden".  
  
-   Der Hauptbericht kann nicht aktualisiert werden, aber ein oder mehrere Unterberichte können aktualisiert werden. Der Hauptbericht wird vom verarbeitet die [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] Berichtsprozessor, aber im gerenderten Bericht wird die Meldung "Fehler: Unterbericht konnte nicht in den Speicherort, an der Unterbericht angezeigt würde, verarbeitet werden".  
  
 Wenn Sie die Fehlermeldung "Fehler: Unterbericht konnte nicht verarbeitet werden", Sie müssen die Definition des Hauptberichts oder des Unterberichts ändern, sodass die Berichte, die von der gleichen Version des berichtsprozessors verarbeitet werden können.  
  
 Für Drillthroughberichte gilt diese Einschränkung nicht, da sie als unabhängige Berichte verarbeitet werden.  
  
##  <a name="bkmk_CRIs"></a> Aktualisieren eines Berichts mit benutzerdefinierten Berichtselementen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichte können benutzerdefinierte Berichtselemente (CRI) enthalten, die von Drittanbietern bereitgestellt und vom Systemadministrator auf dem Computer zur Berichtserstellung und dem Berichtsserver installiert wurden. Berichte, die CRIs enthalten, können auf die folgenden Weisen aktualisiert werden:  
  
-   Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Berichtsserver von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005 wird auf einen [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Berichtsserver aktualisiert. Auf dem Berichtsserver veröffentlichte Berichte werden automatisch bei der ersten Verwendung aktualisiert.  
  
-   Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Bericht von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005 wird auf einen [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Berichtsserver hochgeladen. Der Bericht wird bei seiner ersten Verwendung automatisch aktualisiert.  
  
-   Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bericht wird im Berichts-Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]geöffnet. Es wird eine Sicherungskopie des ursprünglichen Berichts erstellt. Einer der folgenden zwei Fälle tritt auf:  
  
    1.  Alle CRIs im Bericht verfügen über keine nicht unterstützten Funktionen. Die CRIs werden in Berichtselemente im neuen Berichtsdefinitionsformat konvertiert, sodass der gesamte Bericht aktualisiert wird. Wenn Sie die Datei speichern, wird sie im aktuellen RDL-Namespace gespeichert.  
  
    2.  Ein oder mehrere CRIs im Bericht verfügen über nicht unterstützte Funktionen. Ein Dialogfeld fordert den Benutzer zur Angabe auf, ob die CRIs konvertiert oder unverändert beibehalten werden sollen.  
  
     Weitere Informationen hierzu finden Sie unter [Öffnen eines Berichts mit CRIs im Berichts-Designer](#OpeningaReport) weiter hinten in diesem Thema  
  
 Weitere Informationen zum Identifizieren des aktuellen RDL-Namespace für einen Berichtsserver, für [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] oder für einem Bericht finden Sie unter [Suchen der Berichtsdefinitions-Schemaversion (SSRS)](../reports/find-the-report-definition-schema-version-ssrs.md).  
  
### <a name="upgrading-reports-on-a-report-server"></a>Aktualisieren eines Berichts auf einem Berichtsserver  
 Wenn ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Bericht von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005 zum ersten Mal auf einem Berichtsserver ausgeführt wird, der auf einen [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Berichtsserver aktualisiert wurde, wird der Bericht automatisch auf den aktuellen Berichtsdefinitionsnamespace aktualisiert, der von dem Berichtsserver unterstützt wird. Der Bericht kann vor dem Upgrade auf dem Berichtsserver vorhanden gewesen sein, oder der Bericht kann mit dem Berichts-Manager auf den Berichtsserver hochgeladen oder vom Berichts-Designer in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]auf dem Berichtsdesigner veröffentlicht worden sein.  
  
 In der folgenden Tabelle werden die Upgradeaktionen aufgeführt, die vom Berichtsserver für bestimmte Typen von CRIs in einem Bericht ausgeführt werden.  
  
|CRI-Typ|Upgradeaktion des Berichtsservers|  
|--------------|----------------------------------|  
|CRIs von Drittanbietern|Es wird kein Upgrade durchgeführt.<br /><br /> Sie werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsprozessor verarbeitet.|  
|Dundas 2005 Chart CRI ohne nicht unterstützte Funktionen|Die CRIs werden auf das neueste RDL-Schema aktualisiert. Alle Dundas 2005 Chart CRIs werden in Diagrammdatenbereiche konvertiert, die mit [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]kompatibel sind.<br /><br /> Die CRIs werden vom [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] - Berichtsprozessor verarbeitet.|  
|Dundas 2005 Gauge CRI ohne nicht unterstützte Funktionen|Die CRIs werden auf das neueste RDL-Schema aktualisiert. Alle Dundas 2005 Gauge CRIs werden in Messgerätdatenbereiche konvertiert, die mit [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] kompatibel sind.<br /><br /> Die CRIs werden vom [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] - Berichtsprozessor verarbeitet.|  
|Dundas 2005 Chart CRI mit nicht unterstützten Funktionen|Es wird kein Upgrade durchgeführt.<br /><br /> Sie werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsprozessor verarbeitet.|  
|Dundas 2005 Gauge CRI mit nicht unterstützten Funktionen|Es wird kein Upgrade durchgeführt.<br /><br /> Sie werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsprozessor verarbeitet.|  
  
###  <a name="OpeningaReport"></a> Öffnen eines Berichts mit CRIs im Berichts-Designer  
 Wenn Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bericht mit CRIs im Berichts-Designer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]öffnen, wird der Bericht mit dem neuen Berichtsdefinitionsschema aktualisiert. Abhängig von den im Bericht enthaltenen CRIs wird eine der folgenden Aktionen ausgeführt:  
  
-   Es wurden CRIs von Drittanbietern erkannt. Wenn die auf dem Computer zur Berichtserstellung installierte CRI-Version nicht mit dem neuen RDL-Schema kompatibel ist, wird in der Entwurfsoberfläche ein Textfeld mit einem roten X angezeigt. Sie müssen sich an Ihren Systemadministrator wenden, um neue Versionen der CRIs von Drittanbietern zu installieren, die mit dem neuen RDL-Schema kompatibel sind.  
  
-   Es wurden Dundas 2005 Chart oder Gauge CRIs erkannt, und alle Instanzen enthalten unterstützte Funktionen. Alle Dundas 2005 Chart und Gauge CRIs werden in die Diagramm- bzw. Messgerätberichtselemente in Reporting Services konvertiert, die in der Toolbox enthalten sind. Diese werden als systemeigene Diagramm- und Messgerätberichtselemente bezeichnet.  
  
-   Es wurden Dundas 2005 Chart oder Gauge CRIs erkannt, und es sind Instanzen mit nicht unterstützten Funktionen vorhanden. Die nicht unterstützte Funktionalität wird nach diesem Abschnitt beschrieben. Sie können auswählen, ob alle CRIs in systemeigene Berichtselemente konvertiert werden sollen.  
  
    -   Wenn Sie sie konvertieren, wird der Bericht mit dem neuen RDL-Schema aktualisiert, und die Dundas 2005 Chart und Gauge CRIs werden in die entsprechenden Diagramm- bzw. Messgerätberichtselemente konvertiert, wobei die nicht unterstützten Funktionen jedoch entfernt werden. Im gerenderten Bericht werden die CRIs möglicherweise anders dargestellt.  
  
    -   Wenn Sie sie nicht konvertieren, wird der Bericht mit dem neuen RDL-Schema aktualisiert, die CRIs werden jedoch als CRIs von Drittanbietern behandelt. Sie müssen mit dem Systemadministrator und den Drittanbietern zusammenarbeiten, um neue CRIs zu installieren, die mit dem neuen Berichtsschema kompatibel sind. Wenn keine neuen CRIs verfügbar sind, wird im Berichts-Designer ein Textfeld mit einem roten X im Bericht angezeigt.  
  
 Ein vorhandener Bericht lässt sich nur dadurch mit dem neuen Berichtsdefinitionsschema aktualisieren, dass er nach dem Upgrade in der Berichterstellungsumgebung gespeichert wird.  
  
### <a name="unsupported-dundas-2005-chart-custom-report-item-functionality"></a>Nicht unterstützte Funktionalität im Dundas 2005 Chart-Berichtselement  
 Zur nicht unterstützten Funktionalität von Dundas 2005 Chart CRIs gehören folgende Features:  
  
-   Anmerkungen  
  
-   Benutzerdefinierte Legendenelemente  
  
-   Benutzerdefinierte Attribute mit den folgenden Namen:  
  
    -   CUSTOM_CODE_CS  
  
    -   CUSTOM_CODE_VB  
  
    -   CUSTOM_CODE_COMPILED_ASSEMBLY  
  
         Wenn beispielsweise die RDL-Datei den folgenden Abschnitt enthält, müssen Sie diesen vor dem Upgrade entfernen:  
  
        ```  
        <CustomProperty>  
         <Name>CUSTOM_CODE_CS</Name>  
         <Value>dXNpWERwegfdfgiobxxl3bmc... </Value>  
        </CustomProperty>  
        ```  
  
### <a name="unsupported-dundas-2005-gauge-custom-report-item-functionality"></a>Nicht unterstützte Funktionalität im Dundas 2005 Gauge-Berichtselement  
 Zur nicht unterstützten Funktionalität von Dundas 2005 Gauge CRIs gehören folgende Features:  
  
-   Numerische Indikatoren  
  
-   Statusindikatoren  
  
-   Benutzerdefinierte Bilder  
  
###  <a name="bkmk_convertCRIdialog"></a> CRI konvertieren (Dialogfeld)  
 Dieser Bericht enthält benutzerdefinierte Berichtselemente (Custom Report Item, CRI) mit nicht unterstützten Funktionen. CRIs sind Erweiterungen der Berichtsdefinitionssprache (Report Definition Language, RDL) zur Unterstützung benutzerdefinierter Objekte, die Daten in einem Bericht anzeigen. CRIs umfassen Entwurfszeit- und Laufzeitkomponenten, die von Drittanbietern bereitgestellt werden.  
  
> [!NOTE]  
>  Die Entscheidung, benutzerdefinierte Berichtselemente auf einem Berichtsserver zuzulassen, wird vom Systemadministrator getroffen. Zum Anzeigen von CRIs in einem Bericht müssen die CRI-Komponenten auf dem Berichterstellungsserver installiert sein, um einen Bericht als Vorschau anzuzeigen, und auf dem Berichtsserver, um einen veröffentlichten oder hochgeladenen Bericht anzuzeigen. Weitere Informationen finden Sie unter [Benutzerdefinierte Berichtselemente](../custom-report-items/custom-report-items.md) und in der Dokumentation des Softwaredrittanbieters.  
  
 Einige CRIs können im neuen Berichtsdefinitionsformat in Berichtselemente konvertiert werden. Die Liste der CRIs, die konvertiert werden können, finden Sie unter [Upgrading Reports](upgrade-reports.md). Entscheiden Sie anhand der folgenden Liste, ob die CRIs in diesem Bericht konvertiert werden sollen:  
  
-   **Ja** Wählen Sie **Ja** aus, um nach Möglichkeit alle CRIs im Bericht zu konvertieren. Nicht unterstützte Funktionen in den CRIs können nicht aktualisiert werden und werden aus der Berichtsdefinitionsdatei entfernt. Die Liste der nicht unterstützten Funktionen finden Sie unter [Upgrading Reports](upgrade-reports.md). Bei der Anzeige des Berichts werden möglicherweise Unterschiede in der Darstellung der CRIs im Bericht deutlich.  
  
-   **Nein** Wählen Sie **Nein** aus, wenn die CRIs im Bericht nicht konvertiert werden sollen. Diese CRIs können vom Berichtsprozessor nicht in ihrer aktuellen Version angezeigt werden. Wenn der Systemadministrator die Installation einer neuen CRI-Version von einem Softwaredrittanbieter plant, die mit dem neuen Berichtsdefinitionsformat kompatibel ist, sollten Sie **Nein**auswählen. Bis neue Versionen zur Verfügung stehen, werden die CRIs im Bericht als leere Textfelder mit einem roten X dargestellt.  
  
 In beiden Fällen wird der Bericht auf das neue Berichtsdefinitionsformat aktualisiert, und eine Sicherungskopie des ursprünglichen Berichts wird als „*\<Berichtsname>* `-` Backup.rdl“ gespeichert. Wenn Sie den Bericht im Berichterstellungstool speichern, wird der aktualisierte Bericht im neuen Berichtsdefinitionsformat gespeichert. Beim Veröffentlichen des Berichts wird dieser zuerst auf Ihrem Computer gespeichert und dann auf dem Berichtsserver veröffentlicht. Sie veröffentlichen die aktualisierte Version des Berichts auf dem Berichtsserver.  
  
 Wenn Sie den Bericht nicht speichern, bleibt der ursprüngliche Bericht unverändert. Sie können diesen Bericht jedoch nicht in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version von [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] oder in einer Berichterstellungsumgebung bearbeiten, für die ein neueres Berichterstellungsformat verwendet wird. Die ursprüngliche Version des Berichts kann weiterhin ausgeführt werden, indem Sie diese im Berichts-Manager auf einen [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Berichtsserver hochladen. Weitere Informationen finden Sie unter [Hochladen einer Datei oder eines Berichts &#40;Berichts-Manager&#41;](../reports/upload-a-file-or-report-report-manager.md).  
  
 Bei Berichten, die Sie hochladen, statt sie auf einem Berichtsserver zu veröffentlichen, bestimmt der Berichtsprozessor, ob der Bericht bei der ersten Verwendung aktualisiert werden kann. Berichte, die nicht aktualisiert werden können, werden im Abwärtskompatibilitätsmodus verarbeitet und weiterhin wie in der früheren Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren und Migrieren von Reporting Services](upgrade-and-migrate-reporting-services.md)   
 [Wichtige Änderungen in SQL Server Reporting Services in SQLServer 2014](../breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)   
 [Verhaltensänderungen in SQL Server Reporting Services in SQLServer 2014](../behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Nicht mehr unterstützte Funktionen in SQL Server Reporting Services in SQLServer 2014](../discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)   
 [Benutzerdefinierte Berichtselemente](../custom-report-items/custom-report-items.md)   
 [Aktualisieren der Berichtsserver-Datenbank](upgrade-a-report-server-database.md)  
  
  
