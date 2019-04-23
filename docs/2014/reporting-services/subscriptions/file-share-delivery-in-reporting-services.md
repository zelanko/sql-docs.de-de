---
title: Dateifreigabeübermittlung in Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], file share delivery
- file share delivery [Reporting Services]
ms.assetid: 9f338dd3-f68a-4355-b9d7-9b25dacf3b5e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cdc9821d9e1d8b3013b146cba4b509cb744ef9e4
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59967686"
---
# <a name="file-share-delivery-in-reporting-services"></a>Dateifreigabeübermittlung in Reporting Services
  SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthält eine Dateifreigabe-Übermittlungserweiterung, mit deren Hilfe ein Bericht an einen Ordner übermittelt werden kann. Diese Erweiterung ist standardmäßig verfügbar und erfordert keine zusätzliche Konfiguration. Damit die Dateiübermittlung erfolgreich ist, müssen Sie Schreibberechtigungen für den freigegebenen Ordner erteilen. Außerdem müssen Benutzer, die auf die Berichte zugreifen wollen, über Leseberechtigungen für den freigegebenen Ordner verfügen.  
  
 Um einen Bericht an eine Dateifreigabe zu verteilen, definieren Sie entweder ein Standardabonnement oder ein datengesteuertes Abonnement. Es kann jeweils immer nur ein Bericht abonniert und angefordert werden. Erfahren Sie, wie Sie die Dateifreigabeübermittlung in einem datengesteuerten Abonnement verwenden, indem Sie sich den Artikel [Erstellen eines datengesteuerten Abonnements (SSRS-Tutorial)](../create-a-data-driven-subscription-ssrs-tutorial.md) lesen. Zusätzlich sind für das Konto, unter dem Remotedateifreigabe-Abonnements ausgeführt werden, Rechte für die lokale Anmeldung beim [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Computer erforderlich.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus|  
  
 In diesem Thema:  
  
-   [Merkmale eines Berichts, die an einen freigegebenen Ordner übermittelt wird](#bkmk_Characteristics)  
  
-   [Zielordner](#bkmk_target_folders)  
  
-   [Dateiformate](#bkmk_file_formats)  
  
-   [Dateioptionen](#bkmk_file_options)  
  
##  <a name="bkmk_Characteristics"></a> Merkmale eines Berichts, die an einen freigegebenen Ordner übermittelt wird  
 Im Gegensatz zu Berichten, die von einem Berichtsserver gehostet und verwaltet werden, handelt es sich bei Berichten, die an einen freigegebenen Ordner übermittelt werden, um statische Dateien. Interaktive Funktionen, die für den Bericht definiert sind, können bei Berichten, die als Dateien im Dateisystem gespeichert sind, nicht verwendet werden. Interaktive Funktionen werden als statische Elemente dargestellt. Wenn Sie z. B. einen Matrixbericht übermitteln, zeigt die resultierende Datei die oberste Ebene des Berichts an. Es ist nicht möglich, Zeilen und Spalten zu erweitern, um die unterstützenden Daten anzuzeigen. Enthält der Bericht Diagramme, wird die Standardpräsentation verwendet. Wenn der Bericht einen Link zu einem anderen Bericht enthält, wird der Link als statischer Text gerendert. Wenn Sie die interaktiven Funktionen bei einem übermittelten Bericht erhalten möchten, müssen Sie die E-Mail-Übermittlung verwenden. Weitere Informationen finden Sie unter [E-Mail-Übermittlung in Reporting Services](e-mail-delivery-in-reporting-services.md).  
  
##  <a name="bkmk_target_folders"></a> Zielordner  
 Wenn Sie ein Abonnement definieren, das die Dateifreigabeübermittlung verwendet, müssen Sie einen vorhandenen Ordner als Zielordner angeben. Der Berichtsserver erstellt keine Ordner im Dateisystem. Auf den angegebenen Ordner muss über eine Netzwerkverbindung zugegriffen werden können.  
  
 Überprüfen Sie, ob Benutzer, die die Berichte im freigegebenen Order anzeigen, über Leseberechtigungen verfügen.  
  
 Verwenden Sie beim Angeben des Zielordners in einem Abonnement das UNC-Format (Uniform Naming Convention), das den Netzwerknamen des Computers enthält. Der Ordnerpfad darf keine nachgestellten umgekehrten Schrägstriche enthalten. Das folgende Beispiel veranschaulicht einen UNC-Pfad:  
  
```  
\\<servername>\reportarchive\operations\2003  
```  
  
 Beachten Sie beim Erstellen des Ordners die erforderlichen Verbindungslimits. Für den Berichtsserver sind zwei Verbindungen erforderlich. Sie müssen jedoch genügend Verbindungen einfügen, um weitere Benutzer aufnehmen zu können, die Berichte im freigegebenen Ordner öffnen möchten.  
  
##  <a name="bkmk_file_formats"></a> Dateiformate  
 Berichte können in einer Vielzahl von Dateiformaten gerendert werden, z. B. in HTML oder Excel. Um einen Bericht in einem bestimmten Dateiformat zu speichern, wählen Sie das entsprechende Renderingformat aus, wenn Sie Ihr Abonnement erstellen. Beispielsweise wird durch Auswählen von **Excel** der Bericht als [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] -Datei gespeichert. Sie können zwar ein beliebiges unterstütztes Renderingformat auswählen, manche Formate eignen sich jedoch besser zum Rendern einer Datei.  
  
 Wenn Sie die Dateifreigabeübermittlung verwenden, wählen Sie ein Format aus, das den Bericht in einer einzigen Datei übermittelt, bei dem alle Bilder und der zugehörige Inhalt im Bericht enthalten sind. Passende Formate sind Webarchiv, PDF, TIFF und Excel. Verwenden Sie wenn möglich nicht HTML 4.0. Wenn Ihr Bericht Bilder enthält, werden sie beim HTML 4.0-Format nicht in die Datei eingefügt.  
  
##  <a name="bkmk_file_options"></a> Dateioptionen  
 Beim Erstellen eines Abonnements können Sie Optionen auswählen, die bestimmen, wie der Dateiname erstellt wird und ob er im Laufe der Zeit durch einen neuen ersetzt werden soll. Ein vollqualifizierter Dateiname besteht aus drei Teilen: einem Namen, einer Erweiterung sowie Text oder einer Zahl, der bzw. die an den Namen angefügt wird, um einen eindeutigen Dateinamen zu erzeugen. Mit Überschreibungsoptionen legen Sie fest, ob dem Dateinamen Text oder eine Zahl hinzugefügt wird.  
  
 Der Dateiname basiert auf dem Berichtsnamen, Sie können jedoch im Abonnement einen benutzerdefinierten Namen bereitstellen. Die Erweiterung ist optional, aber wenn Sie sie angeben, erstellt der Berichtsserver eine dem Renderingformat entsprechende Erweiterung.  
  
 Sie können Optionen zum Überschreiben angeben, um den Dateinamen bei jeder Berichtsübermittlung oder Erstellung einer neuen Datei wiederzuverwenden. Zum Überschreiben der Datei müssen Sie den gleichen Dateinamen und die gleiche Erweiterung verwenden.  
  
 Ein andere Möglichkeit, eindeutige Dateinamen für jede Übermittlung zu erstellen, ist das Einschließen eines Timestamps in den Dateinamen. Fügen Sie zu diesem Zweck die `@timestamp` -Variable dem Dateinamen (z. B. *CompanySales@timestamp*). Auf diese Weise ist der Dateiname per definitionem eindeutig und wird daher niemals überschrieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen, ändern und Löschen von Standardabonnements &#40;Reporting Services im einheitlichen Modus&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md)  
  
  
