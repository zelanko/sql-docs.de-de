---
title: 'Lektion 1: Erstellen der DQS-Wissensdatenbank für Lieferanten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 78825ccb-30fc-463c-8140-435532e2ecd2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e9421f568dae28895eb40b397d5e2589fafe0186
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054333"
---
# <a name="lesson-1-creating-the-suppliers-dqs-knowledge-base"></a>Lektion 1: Erstellen der DQS-Wissensdatenbank „Suppliers“
  In dieser Lektion erstellen Sie eine DQS-Wissensdatenbank mit dem Namen **Suppliers** und den Kenntnissen (Metadaten) zu Lieferantendaten. Sie verwenden die Wissensdatenbank, um die Bereinigungs- und Abgleichsaktivitäten für Eingabelieferantendaten auszuführen. Die Bereinigungsaktivität identifiziert falsche/ungültige Daten, korrigiert falsche Daten, schlägt Korrekturen vor/macht Vorschläge, standardisiert die Daten und wertet die Daten durch weitere Informationen auf. Die Abgleichsaktivität vergleicht Daten und identifiziert ähnliche (aber leicht abweichende) Datensätze in den Daten, wodurch Sie Datenduplikate entfernen können.  
  
 Sie können sowohl interaktive als auch computerunterstützte Prozesse verwenden, um eine Wissensdatenbank zu erstellen, aufzubauen und zu verwalten. Wissen in einer Wissensdatenbank wird in Domänen verwaltet, die jeweils für ein Datenfeld in den Daten spezifisch sind, die Sie bereinigen und/oder abgleichen möchten.  
  
 In dieser Lektion führen Sie die folgenden Aufgaben aus, um die Wissensdatenbank **Suppliers** zu erstellen:  
  
-   Erstellen Sie eine DQS-Wissensdatenbank namens **Suppliers**. Sie können eine Wissensdatenbank auf verschiedene Arten erstellen. Sie können eine Wissensdatenbank wie folgt erstellen: von Grund auf, basierend auf einer vorhandenen Wissensdatenbank, durch den Import einer DQS-Datei (.dqs), die eine vordefinierte und exportierte Wissensdatenbank enthält, oder durch eine Wissensermittlungsaktivität für Beispieldaten. In diesem Lernprogramm erstellen Sie die Wissensdatenbank von Grund auf.  
  
-   Erstellen Sie Domänen in der Wissensdatenbank **Suppliers** , die Sie zum Bereinigen von Daten verwenden, und vergleichen Sie Daten, um Duplikate zu identifizieren. Erstellen Sie Domänen für Datenfelder, die Sie in Bereinigungs- und Abgleichsaktivitäten verwenden möchten, nicht für alle Datenfelder in den Daten.  
  
-   Fügen Sie einer Domäne Werte hinzu, indem Sie Werte manuell hinzufügen, Werte aus einer Excel-Datei importieren, eine Wissensermittlungsaktivität für Beispieldaten ausführen und Projektwerte aus einem Bereinigungsprojekt importieren. Sie können Domänenwerte auch importieren, indem Sie eine DQS-Datei mit Domäneneigenschaften und -werten importieren, die Sie nicht im Lernprogramm ausführen.  
  
-   Legen Sie Regeln für eine Domäne fest. Eine Domänenregel ist eine Bedingung, mit der Domänenwerte von DQS überprüft, korrigiert und standardisiert werden.  
  
-   Legen Sie begriffsbasierte Beziehungen für eine Domäne fest. Mithilfe von begriffsbasierten Beziehungen können Sie eine Korrektur an einem Begriff vornehmen, der Teil eines Werts in einer Domäne ist. Beispielsweise ist der Wert von "" in der **Datei** "" von "". Dies ist bei der Standardisierung der Daten sowie der Identifizierung von Duplikaten hilfreich. Beispielsweise können bei der Integration von "Configuration Manager **" und "** Configuration Manager **" als** Duplikate betrachtet werden.  
  
-   Geben Sie Synonyme in Domänenwerten an. Sie können zwei oder mehr Werte als Synonyme und einen davon als führenden Wert festlegen, der die Synonymwerte während einer Bereinigungsaktivität ersetzt, um die Daten zu standardisieren.  
  
-   Erstellen Sie eine Verbunddomäne namens "Address Validation", die die Domänen "Address line", "City", "State" und "Zip" umfasst. Eine Verbunddomäne ist eine Domäne, die aus einer oder mehreren einzelnen Domänen besteht. Sie können mit ihr eine Regel erstellen, die mehrere Domänen umfasst. Sie können beispielsweise eine Regel definieren: Wenn City Los Angeles ist, muss State CA sein, wobei City und State zwei separate Domänen sind.  
  
-   Konfigurieren und verwenden Sie einen Reference Data Service. Die Funktion "Reference Data Service" in Data Quality Services (DQS) ermöglicht es Ihnen, Reference Data Service-Drittanbieter zu abonnieren und Ihre Geschäftsdaten durch das Überprüfen gegen hochwertige Daten dieser Anbieter leicht zu bereinigen und zu erweitern. Sie können Dienste von führenden DQS-Anbietern innerhalb von DQS verwenden, um Ihre Daten während des Bereinigungsprozesses zu standardisieren, zu korrigieren und zu erweitern. In diesem Tutorial erfahren Sie, wie Sie die DQS-Umgebung so konfigurieren, dass Sie einen Verweis Datendienst auf Azure Marketplace verwendet, und den mit der Verbund Domäne der Adressvalidierung verknüpften Dienst verwenden, um Adressdaten zu bereinigen.  
  
-   Veröffentlichen Sie die Wissensdatenbank, damit die Wissensdatenbank in Bereinigungs- und Abgleichsaktivitäten verwendet werden kann.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 1: Erstellen von Wissensdatenbanken und Domänen](../../2014/tutorials/task-1-creating-a-knowledge-base-and-domains.md)  
  
  
