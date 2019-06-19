---
title: "Lektion 1: Erstellen der DQS-Wissensdatenbank ' Suppliers ' | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 78825ccb-30fc-463c-8140-435532e2ecd2
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 6e25b57bce84876de1119ec52ad068602cd5cf13
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65485583"
---
# <a name="lesson-1-creating-the-suppliers-dqs-knowledge-base"></a>Lektion 1: Erstellen der DQS-Wissensdatenbank „Suppliers“
  In dieser Lektion erstellen Sie eine DQS-Wissensdatenbank namens **Lieferanten** mit dem Wissen (Metadaten) über Lieferantendaten. Sie verwenden die Wissensdatenbank, um die Bereinigungs- und Abgleichsaktivitäten für Eingabelieferantendaten auszuführen. Die Bereinigungsaktivität identifiziert falsche/ungültige Daten, korrigiert falsche Daten, schlägt Korrekturen vor/macht Vorschläge, standardisiert die Daten und wertet die Daten durch weitere Informationen auf. Die Abgleichsaktivität vergleicht Daten und identifiziert ähnliche (aber leicht abweichende) Datensätze in den Daten, wodurch Sie Datenduplikate entfernen können.  
  
 Sie können sowohl interaktive als auch computerunterstützte Prozesse verwenden, um eine Wissensdatenbank zu erstellen, aufzubauen und zu verwalten. Wissen in einer Wissensdatenbank wird in Domänen verwaltet, die jeweils für ein Datenfeld in den Daten spezifisch sind, die Sie bereinigen und/oder abgleichen möchten.  
  
 In dieser Lektion führen Sie die folgenden Aufgaben zum Erstellen der **Lieferanten** Wissensdatenbank:  
  
-   Erstellen Sie eine DQS-Wissensdatenbank namens **Lieferanten**. Sie können eine Wissensdatenbank auf verschiedene Arten erstellen. Sie können eine Wissensdatenbank wie folgt erstellen: von Grund auf, basierend auf einer vorhandenen Wissensdatenbank, durch den Import einer DQS-Datei (.dqs), die eine vordefinierte und exportierte Wissensdatenbank enthält, oder durch eine Wissensermittlungsaktivität für Beispieldaten. In diesem Lernprogramm erstellen Sie die Wissensdatenbank von Grund auf.  
  
-   Erstellen Sie Domänen in der **Lieferanten** Knowledge Base, dass Sie für die Bereinigung und Abgleich von Daten verwenden, um Duplikate zu identifizieren. Erstellen Sie Domänen für Datenfelder, die Sie in Bereinigungs- und Abgleichsaktivitäten verwenden möchten, nicht für alle Datenfelder in den Daten.  
  
-   Fügen Sie einer Domäne Werte hinzu, indem Sie Werte manuell hinzufügen, Werte aus einer Excel-Datei importieren, eine Wissensermittlungsaktivität für Beispieldaten ausführen und Projektwerte aus einem Bereinigungsprojekt importieren. Sie können Domänenwerte auch importieren, indem Sie eine DQS-Datei mit Domäneneigenschaften und -werten importieren, die Sie nicht im Lernprogramm ausführen.  
  
-   Legen Sie Regeln für eine Domäne fest. Eine Domänenregel ist eine Bedingung, mit der Domänenwerte von DQS überprüft, korrigiert und standardisiert werden.  
  
-   Legen Sie begriffsbasierte Beziehungen für eine Domäne fest. Mithilfe von begriffsbasierten Beziehungen können Sie eine Korrektur an einem Begriff vornehmen, der Teil eines Werts in einer Domäne ist. In den Wert beispielsweise **Contoso Inc., Inc.** ist ein Ausdruck, der als Incorporated definiert werden kann. Dies ist bei der Standardisierung der Daten sowie der Identifizierung von Duplikaten hilfreich. Z. B. **Contoso Inc.** und **Contoso Incorporated** als Duplikate angesehen werden können.  
  
-   Geben Sie Synonyme in Domänenwerten an. Sie können zwei oder mehr Werte als Synonyme und einen davon als führenden Wert festlegen, der die Synonymwerte während einer Bereinigungsaktivität ersetzt, um die Daten zu standardisieren.  
  
-   Erstellen Sie eine Verbunddomäne namens "Address Validation", die die Domänen "Address line", "City", "State" und "Zip" umfasst. Eine Verbunddomäne ist eine Domäne, die aus einer oder mehreren einzelnen Domänen besteht. Sie können mit ihr eine Regel erstellen, die mehrere Domänen umfasst. Sie können beispielsweise eine Regel definieren: Wenn City Los Angeles ist, muss State CA sein, wobei City und State zwei separate Domänen sind.  
  
-   Konfigurieren und verwenden Sie einen Reference Data Service. Die Funktion "Reference Data Service" in Data Quality Services (DQS) ermöglicht es Ihnen, Reference Data Service-Drittanbieter zu abonnieren und Ihre Geschäftsdaten durch das Überprüfen gegen hochwertige Daten dieser Anbieter leicht zu bereinigen und zu erweitern. Sie können Dienste von führenden DQS-Anbietern innerhalb von DQS verwenden, um Ihre Daten während des Bereinigungsprozesses zu standardisieren, zu korrigieren und zu erweitern. In diesem Lernprogramm erfahren Sie, wie Sie die DQS-Umgebung konfigurieren, um einen Reference Data Service in Windows Azure Marketplace zu verwenden und den mit der Verbunddomäne "Address Validation" verknüpften Dienst zu erstellen, um Adressdaten zu bereinigen.  
  
-   Veröffentlichen Sie die Wissensdatenbank, damit die Wissensdatenbank in Bereinigungs- und Abgleichsaktivitäten verwendet werden kann.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 1: Erstellen eine Wissensdatenbank und Domänen](../../2014/tutorials/task-1-creating-a-knowledge-base-and-domains.md)  
  
  
