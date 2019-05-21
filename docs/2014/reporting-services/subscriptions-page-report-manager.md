---
title: Seite "Abonnements" (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: cf3a6bd0-e0b2-4875-a532-63ef34cfa860
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: efa4c0758ed85008ccb04b30a8dcd8e24ed54208
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62511365"
---
# <a name="subscriptions-page-report-manager"></a>Abonnements (Seite) (Berichts-Manager)
  Mithilfe der Seite Abonnements können Sie alle Abonnements für den aktuellen Bericht oder die aktuelle freigegebene Datenquelle anzeigen. Wenn Sie über ausreichende Berechtigungen verfügen (wie sie durch den Task "Alle Abonnements verwalten" übertragen werden), können Sie die Abonnements aller Benutzer anzeigen. Ansonsten sind auf dieser Seite nur Ihre Abonnements aufgeführt.  
  
> [!NOTE]  
>  Auch andere Seiten enthalten Abonnementinformationen. Weitere Informationen finden Sie unter [Seite "Meine Abonnements" &#40;Berichts-Manager&#41; ](../../2014/reporting-services/my-subscriptions-page-report-manager.md) auf all Ihren Abonnements zentral oder [neues Abonnement oder Abonnement-Seite bearbeiten &#40;Berichts-Manager&#41; ](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md) erstellen oder Bearbeiten eines Abonnements.  
  
 Einige Optionen werden nur angezeigt, wenn entsprechende Abonnements vorhanden sind. Falls keine Abonnements definiert sind und Sie von einem Bericht aus auf diese Seite zugreifen, werden auf dieser Seite nur die Optionen **Neues Abonnement** und **Neues datengesteuertes Abonnement** angezeigt.  
  
 Bevor Sie ein neues Abonnement erstellen können, müssen Sie sicherstellen, dass die Berichtsdatenquelle gespeicherte Anmeldeinformationen verwendet. Zum Speichern von Anmeldeinformationen verwenden Sie die Eigenschaftenseite Datenquelle. Weitere Informationen finden Sie unter [Data Sources – Seite "Eigenschaften" &#40;Berichts-Manager&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md).  
  
> [!NOTE]  
>  Diese Funktion ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
### <a name="to-open-the-subscriptions-page-for-report"></a>So öffnen Sie die Seite 'Abonnements' für einen Bericht  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Bericht, für den Sie ein Abonnement anzeigen oder konfigurieren möchten.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für den Bericht geöffnet.  
  
4.  Wählen Sie die Registerkarte **Abonnements** aus.  
  
## <a name="options"></a>Optionen  
 **Löschen**  
 Klicken Sie auf diese Schaltfläche, um ein Abonnement zu löschen. Bevor Sie Abonnements löschen, aktivieren Sie das Kontrollkästchen neben den zu löschenden Abonnements.  
  
 **Neues Abonnement**  
 Klicken Sie auf diese Schaltfläche, um ein neues Abonnement für den aktuellen Bericht zu erstellen. Diese Schaltfläche ist aktiviert, wenn der Bericht gespeicherte oder gar keine Anmeldeinformationen verwendet. Diese Schaltfläche ist nicht verfügbar, wenn Sie die Seite Abonnements für eine freigegebene Datenquelle öffnen.  
  
 **Neues datengesteuertes Abonnement**  
 Klicken Sie auf diese Schaltfläche, um eine Abonnentenliste und Übermittlungsoptionen mithilfe eines Befehls oder einer Abfrage in einem Datenspeicher zu generieren, der diese Informationen enthält. Diese Schaltfläche ist aktiviert, wenn der Bericht gespeicherte oder gar keine Anmeldeinformationen verwendet. Diese Schaltfläche ist nicht verfügbar, wenn Sie die Seite Abonnements für eine freigegebene Datenquelle öffnen.  
  
 **Bearbeiten**  
 Klicken Sie auf diese Schaltfläche, um die Beschreibung anzuzeigen oder zu bearbeiten.  
  
 **Bericht**  
 Wenn Sie diese Seite aus einer freigegebenen Datenquelle öffnen, identifiziert diese Spalte den Bericht, für den das Abonnement definiert ist. Die Spalte **Ordner** identifiziert den Speicherort des Berichts.  
  
 **Beschreibung**  
 Zeigt eine Beschreibung des Abonnements an.  
  
 **Trigger**  
 Identifiziert Kriterien, die die Ausführung des Abonnements auslösen. Ein **TimedSubscription** -Trigger basiert auf einem Zeitplan, der den Zeitpunkt der Ausführung des Abonnements definiert. Ein **SnapshotUpdated** -Trigger basiert auf dem Update einer Berichtsmomentaufnahme.  
  
 **Besitzer**  
 Zeigt den Namen des Benutzers an, der das Abonnement erstellt hat.  
  
 **Zuletzt ausgeführt**  
 Zeigt den Zeitpunkt der letzten Verarbeitung des Abonnements an.  
  
 **Status**  
 Zeigt den Status des Abonnements an. Der Statuswert ist normalerweise Neu oder der Zeitpunkt (Datum und Uhrzeit), zu dem das Abonnement zuletzt ausgeführt wurde.  
  
 Der Statuswert "Bad Data" tritt auf, wenn das Abonnement einen Zeiger auf verschlüsselte Werte enthält, die nicht mehr gültig sind (d. h. auf gespeicherte Anmeldeinformationen, die zur Ausführung des Berichts verwendet werden). Vorhandene verschlüsselte Werte werden unbrauchbar, wenn die zur Ver- oder Entschlüsselung von Daten verwendeten symmetrischen Schlüssel auf dem Berichtsserver erneut erstellt werden.  
  
 Wenn ein Abonnement deaktiviert wurde, kann es nicht verarbeitet werden. Um ein Abonnement zu aktualisieren und wieder funktionsfähig zu machen, müssen Sie es öffnen und speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Erstellen, ändern und Löschen von Standardabonnements &#40;Reporting Services im einheitlichen Modus&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md)   
 [Erstellen, Ändern oder Löschen von Zeitplänen](subscriptions/create-modify-and-delete-schedules.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
