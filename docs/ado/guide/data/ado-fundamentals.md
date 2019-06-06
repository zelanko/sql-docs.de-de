---
title: ADO-Grundlagen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: d6a66928-e68f-4c38-b87a-838c5de50a28
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 155e1e810309ee4efa40badac55ca749a4329182
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702338"
---
# <a name="ado-fundamentals"></a>ADO-Grundlagen
ADO, bietet Entwicklern ein leistungsfähiges, logische Objektmodell zum programmgesteuerten Zugriff auf, bearbeiten und Aktualisieren von Daten aus einer Vielzahl von Datenquellen über OLE DB-Schnittstellen. Die häufigste Verwendung von ADO, werden Abfragen einer Tabelle oder Tabellen in einer relationalen Datenbank, abrufen und Anzeigen der Ergebnisse in einer Anwendung und vielleicht können Benutzer vornehmen und Speichern von Änderungen an den Daten ab. Andere Aufgaben umfassen Folgendes:  
  
-   Abfragen einer Datenbank mithilfe von SQL und zum Anzeigen der Ergebnisse an.  
  
-   Zugreifen auf Informationen in einem Dateispeicher über das Internet ein.  
  
-   Bearbeiten von Nachrichten und Ordnern in einem e-Mail-System ein.  
  
-   Speichern von Daten aus einer Datenbank in eine XML-Datei.  
  
-   Ausführen von Befehlen, die durch XML-Code beschrieben und das Abrufen eines XML-Streams.  
  
-   Speichern von Daten in einem Binär- oder XML-Stream.  
  
-   Da der Benutzer zu überprüfen und Ändern von Daten in Datenbanktabellen.  
  
-   Erstellen und wiederverwenden parametrisierter Datenbankbefehle.  
  
-   Ausführen von gespeicherten Prozeduren.  
  
-   Erstellen dynamisch eine flexible Struktur, mit dem Namen einer **Recordset**, um zu von aufzunehmen, navigieren und Bearbeiten von Daten.  
  
-   Ausführen von Vorgängen der Transaktionsdatenbank.  
  
-   Filtern und Sortieren lokale Kopien von Datenbankinformationen basierend auf Kriterien der Laufzeit.  
  
-   Erstellen und Bearbeiten von hierarchischen ergibt sich aus Datenbanken.  
  
-   Binden Datenbankfelder an Daten unterstützenden Komponenten an.  
  
-   Erstellen von remote getrennt **Recordsets**.  
  
 ADO verfügbar macht, eine Vielzahl von Optionen und Einstellungen auf diese Flexibilität zu bieten. Aus diesem Grund ist es wichtig, einen methodischen Ansatz für die Informationen zum Verwenden von ADO in einer Anwendung, Ihre Ziele in überschaubare Teile unterteilen.  
  
 Vier primäre Vorgänge sind in den meisten Anwendungen, die ADO verwenden beteiligt: Abrufen von Daten, untersuchen von Daten, Daten bearbeiten und Aktualisieren von Daten. Diese Vorgänge werden im Detail weiter unten in diesem Abschnitt überprüft.  
  
 Aber bevor wir diese Details erläutern, zeigen wir eine Übersicht über die ADO-Objektmodell und eine einfache ADO-Anwendung, die in die Microsoft® Visual Basic geschrieben ist, und führt jeden der vier primäre ADO-Vorgänge:  
  
-   [ADO-Objekte und Sammlungen](../../../ado/guide/data/ado-objects-and-collections.md)  
  
-   [HelloData: Eine einfache ADO-Anwendung](../../../ado/guide/data/hellodata-a-simple-ado-application.md)  
  
-   [OLE DB-Anbieter](../../../ado/guide/data/ole-db-providers-ado.md)  
  
-   [Fehler](../../../ado/guide/data/errors-ado.md)
