---
title: Die Seite Meine Abonnements (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 491a85a3-f323-4155-a0a8-de2779899995
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 75d662f677ee2b6bbab8e445804ca7f142b5c034
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66108187"
---
# <a name="my-subscriptions-page-report-manager"></a>Meine Abonnements (Seite, Berichts-Manager)
  Auf der Seite Meine Abonnements können Sie alle eigenen Abonnements zentral anzeigen. Von dieser Seite aus können Sie auf Ihre Abonnements zugreifen und diese ändern oder löschen. Als eigene Abonnements gelten nur die von Ihnen erstellten Abonnements. Sie können weder auf die Abonnements anderer Benutzer zugreifen noch auf Abonnements, die Sie zwar verwenden, deren Eigentümer Sie aber nicht sind (dies ist z. B. der Fall, wenn Ihr Name zu einem vorhandenen Abonnement hinzugefügt wird, das durch einen anderen Benutzer definiert wurde). Das Erstellen von Abonnements ist auf dieser Seite nicht möglich. Weitere Informationen zum Erstellen von Abonnements finden Sie unter den [neues Abonnement oder Abonnement-Seite bearbeiten &#40;Berichts-Manager&#41;](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md).  
  
 Standardmäßig werden Abonnements in alphabetischer Reihenfolge nach Berichtsname sortiert. Klicken Sie auf eine andere Spaltenüberschrift, um die Sortierreihenfolge der Abonnements zu ändern. Falls keine Abonnements vorhanden sind oder die Berechtigung zum Erstellen oder Verwalten von Abonnements deaktiviert ist, werden auf dieser Seite keine Abonnements angezeigt.  
  
> [!NOTE]  
>  Diese Funktion ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
### <a name="to-open-the-my-subscriptions-page"></a>So öffnen Sie die Seite 'Meine Abonnements'  
  
1.  Öffnen Sie den Berichts-Manager.  
  
2.  Klicken Sie am oberen Rand der Seite in der rechten Ecke auf Meine Abonnements.  
  
    > [!NOTE]  
    >  Die Seite Meine Abonnements ist auch verfügbar, wenn Sie nicht über die Berechtigung zum Erstellen von Abonnements verfügen.  
  
## <a name="options"></a>Optionen  
 **Löschen**  
 Aktivieren Sie das Kontrollkästchen neben dem Abonnement, das Sie löschen möchten, und klicken Sie auf **Löschen**.  
  
 **Bearbeiten**  
 Klicken Sie auf diese Schaltfläche, um die Beschreibung anzuzeigen oder zu bearbeiten.  
  
 **Bericht**  
 Zeigt den Bericht an, der in dem Abonnement angegeben wurde. Klicken Sie auf den Berichtsnamen, um den Bericht anzuzeigen.  
  
 **Beschreibung**  
 Zeigt eine Beschreibung des Abonnements an. Klicken Sie auf die Beschreibung, um die Abonnementinformationen für den Bericht anzuzeigen oder zu bearbeiten.  
  
 **Ordner**  
 Zeigt den Ordner an, der den im Abonnement angegebenen Bericht enthält. Klicken Sie auf den Ordnernamen, um den Inhalt des Ordners anzuzeigen.  
  
 **Trigger**  
 Identifiziert Kriterien, die die Ausführung des Abonnements auslösen. Ein **TimedSubscription** -Trigger basiert auf einem Zeitplan, der den Zeitpunkt der Ausführung des Abonnements definiert. Ein **SnapshotUpdated** -Trigger basiert auf dem Update einer Berichtsmomentaufnahme.  
  
 **Zuletzt ausgeführt**  
 Zeigt den Zeitpunkt der letzten Verarbeitung des Abonnements an.  
  
 **Status**  
 Zeigt den Status des Abonnements an. Der Statuswert ist normalerweise "Neu" oder der Zeitpunkt (Datum und Uhrzeit), zu dem das Abonnement zuletzt ausgeführt wurde.  
  
 Der Statuswert "Bad Data" tritt auf, wenn das Abonnement einen Zeiger auf verschlüsselte Werte enthält, die nicht mehr gültig sind (d. h. auf gespeicherte Anmeldeinformationen, die zur Ausführung des Berichts verwendet werden). Vorhandene verschlüsselte Werte werden unbrauchbar, wenn die zur Ver- oder Entschlüsselung von Daten verwendeten symmetrischen Schlüssel auf dem Berichtsserver erneut erstellt werden.  
  
 Wenn ein Abonnement deaktiviert wurde, kann es nicht verarbeitet werden. Um ein Abonnement zu aktualisieren und wieder funktionsfähig zu machen, müssen Sie es öffnen und speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
