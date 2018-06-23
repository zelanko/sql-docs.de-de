---
title: Neues Abonnement oder Abonnement bearbeiten (Berichts-Manager) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e02d6529-ce67-4305-b7f0-433997e99c21
caps.latest.revision: 38
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: af32c10bd6c18a4cafc46ccba36859413942c98d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161974"
---
# <a name="new-subscription-or-edit-subscription-page-report-manager"></a>Neues Abonnement oder Abonnement bearbeiten (Berichts-Manager)
  Mithilfe der Seite Neues Abonnement oder Abonnement bearbeiten können Sie ein neues Abonnement erstellen oder ein vorhandenes Abonnement für einen Bericht bearbeiten. Abhängig von Ihrer Rollenzuweisung stehen auf dieser Seite unterschiedliche Optionen zur Verfügung. Benutzer mit erweiterten Berechtigungen können zusätzliche Optionen verwenden.  
  
 Abonnements werden nur für Berichte unterstützt, die unbeaufsichtigt ausgeführt werden können. Der Bericht muss zumindest gespeicherte oder gar keine Anmeldeinformationen verwenden. Wenn der Bericht Parameter verwendet, muss ein Standardwert angegeben werden. Abonnements können inaktiv werden, wenn die Berichtsausführungseinstellungen geändert oder die von den Parametereigenschaften verwendeten Standardwerte entfernt werden. Weitere Informationen finden Sie unter [erstellen und Verwalten von Abonnements für Berichtsserver im einheitlichen Modus](../../2014/reporting-services/create-manage-subscriptions-native-mode-report-servers.md).  
  
> [!NOTE]  
>  Diese Funktion ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
### <a name="to-open-the-new-subscription-or-edit-subscription-page"></a>So öffnen Sie die Seite Neues Abonnement oder Abonnement bearbeiten  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Bericht, für den Sie ein Abonnement hinzufügen möchten.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
3.  Führen Sie im Dropdownmenü einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für den Bericht geöffnet. Wählen Sie dann die Registerkarte **Abonnements** aus. Klicken Sie auf der Symbolleiste auf **neues Abonnement**, oder wählen Sie ein vorhandenes Abonnement, und klicken Sie auf **bearbeiten**.  
  
    -   Klicken Sie auf **Abonnieren**. Dadurch wird die Seite **Neues Abonnement** für den Bericht geöffnet.  
  
## <a name="options"></a>Tastatur  
 **Übermittelt von**  
 Wählen Sie die Übermittlungserweiterung aus, die zum Verteilen des Berichts verwendet werden soll. Abhängig von der ausgewählten Übermittlungserweiterung werden die folgenden Einstellungen angezeigt:  
  
-   E-Mail-Abonnements stellen Felder bereit, die den Benutzern von E-Mail vertraut sind (z. B. die Felder **An**, **Betreff**und **Priorität** ). Geben Sie **Bericht einschließen** an, um den Bericht einzubetten oder anzufügen, oder wählen Sie **Link einschließen** aus, um einem Bericht eine URL hinzuzufügen. Mithilfe von **Renderformat** können Sie ein Präsentationsformat für den angefügten oder eingebetteten Bericht auswählen.  
  
-   Dateifreigabeabonnements stellen Felder bereit, die es Ihnen ermöglichen, einen Zielspeicherort anzugeben. Jeder beliebige Bericht kann an eine Dateifreigabe übermittelt werden. Berichte, die interaktive Funktionen unterstützen (einschließlich Matrixberichte, in denen ein Drilldown zu unterstützenden Zeilen und Spalten möglich ist), werden jedoch als statische Dateien dargestellt. Drilldownzeilen und -spalten können in einer statischen Datei nicht angezeigt werden. Der dateifreigabename muss im Uniform Naming Convention (UNC)-Format angegeben werden (z. B. \\\mycomputer\public\myreportfiles). Der Pfadname darf keinen abschließenden umgekehrten Schrägstrich enthalten. Die Berichtsdatei wird in einem Dateiformat ausgegeben, das auf dem Renderformat basiert. Wenn Sie beispielsweise **Excel**auswählen, wird der Bericht als XLS-Datei ausgegeben.  
  
 Die Verfügbarkeit einer Übermittlungserweiterung hängt davon ab, ob sie auf dem Berichtsserver installiert und konfiguriert ist. Berichtsserver-E-Mail stellt die Standardübermittlungserweiterung dar. Sie muss jedoch konfiguriert werden, bevor Sie sie verwenden können. Die Dateifreigabeübermittlung erfordert keine Konfiguration. Sie müssen jedoch einen freigegebenen Ordner definieren, bevor Sie sie verwenden können.  
  
## <a name="subscription-processing-options"></a>Optionen für die Abonnementverarbeitung  
 Mithilfe dieser Einstellungen können Sie Bedingungen für die Verarbeitung des Abonnements definieren. Einige der Optionen stehen nur für Berichte zur Verfügung, die Parameter verwenden oder die als Momentaufnahmen zur Berichtsausführung ausgeführt werden.  
  
 **Wenn der Berichtsinhalt aktualisiert wurde**  
 Wählen Sie diese Option aus, um eine Berichtsmomentaufnahme zu abonnieren, der auf der Grundlage eines Zeitplans aktualisiert wird. Diese Option wird nur angezeigt, wenn Sie einen Bericht abonnieren, der als Momentaufnahme zur Berichtsausführung ausgeführt wird. Der Inhalt für eine Momentaufnahme zur Berichtsausführung wird in der Regel gemäß einem Zeitplan aktualisiert. Für Berichte, die in diesem Modus ausgeführt werden, können Sie definieren, dass das Abonnement nach der Aktualisierung der Momentaufnahme ausgeführt wird.  
  
 **Wenn die geplante berichtsausführung abgeschlossen ist.**  
 Erstellen Sie einen Zeitplan, mit dem bestimmt wird, wann das Abonnement verarbeitet wird.  
  
 **Nach einem freigegebenen Zeitplan**  
 Wählen Sie einen definierten Zeitplan zur Verarbeitung des Abonnements aus.  
  
 **Parameterwerte eingeben**  
 Verwenden Sie diese Option, wenn Sie einen Bericht mit Parametern abonnieren. Diese Option steht nur für parametrisierte Berichte zur Verfügung. Beim Abonnieren eines parametrisierten Berichts können Sie die Parameterwerte angeben, mit deren Hilfe die Berichtsversion erstellt wird, die durch das Abonnement übermittelt wird. Sie können z. B. eine Regionalkennzahl angeben, um Vertriebsdaten für eine bestimmte Region auszuwählen. Wenn Sie keinen Wert angeben, wird der Standardwert verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung &#40;SSRS-Konfigurations-Manager&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)   
 [Berichts-Manager &#40;SSRS im einheitlichen Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Erstellen, Ändern oder Löschen von Zeitplänen](subscriptions/create-modify-and-delete-schedules.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  