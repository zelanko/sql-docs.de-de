---
description: ADO-Grundlagen
title: ADO-Grundlagen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: d6a66928-e68f-4c38-b87a-838c5de50a28
author: rothja
ms.author: jroth
ms.openlocfilehash: dedb841f9889d71da89107766ff26e3f870d1193
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991661"
---
# <a name="ado-fundamentals"></a>ADO-Grundlagen
ADO bietet Entwicklern ein leistungsfähiges, logisches Objektmodell für den programmgesteuerten Zugriff auf, das Bearbeiten und Aktualisieren von Daten aus einer Vielzahl von Datenquellen über OLE DB Systemschnittstellen. Die häufigste Verwendung von ADO besteht darin, eine Tabelle oder Tabellen in einer relationalen Datenbank abzufragen, die Ergebnisse in einer Anwendung abzurufen und anzuzeigen und möglicherweise Benutzer Änderungen an den Daten vorzunehmen. Andere Aufgaben umfassen Folgendes:  
  
-   Abfragen einer Datenbank mithilfe von SQL und Anzeigen der Ergebnisse.  
  
-   Zugreifen auf Informationen in einem Dateispeicher über das Internet.  
  
-   Bearbeiten von Nachrichten und Ordnern in einem e-Mail-System.  
  
-   Speichern von Daten aus einer Datenbank in einer XML-Datei.  
  
-   Ausführen von mit XML beschriebenen Befehlen und Abrufen eines XML-Streams.  
  
-   Speichern von Daten in einem binären oder XML-Stream.  
  
-   Ermöglicht einem Benutzer das überprüfen und Ändern von Daten in Datenbanktabellen.  
  
-   Erstellen und wieder verwenden von parametrisierten Daten Bank Befehlen.  
  
-   Ausführen gespeicherter Prozeduren.  
  
-   Dynamisches Erstellen einer flexiblen Struktur, die als **Recordset**bezeichnet wird, um Daten zu speichern, zu navigieren und zu bearbeiten.  
  
-   Ausführen von transaktionalen Daten Bank Vorgängen.  
  
-   Filtern und Sortieren von lokalen Kopien von Datenbankinformationen basierend auf Lauf Zeit Kriterien  
  
-   Erstellen und Bearbeiten von hierarchischen Ergebnissen aus Datenbanken.  
  
-   Binden von Datenbankfeldern an Daten abhängige Komponenten.  
  
-   Erstellen von Remote getrennten **Recordsets**.  
  
 ADO macht eine Vielzahl von Optionen und Einstellungen verfügbar, um eine solche Flexibilität bereitzustellen. Daher ist es wichtig, eine methodische Herangehensweise an die Verwendung von ADO in einer Anwendung zu treffen und die einzelnen Ziele in verwaltbare Teile aufzuteilen.  
  
 Vier primäre Vorgänge sind an den meisten Anwendungen beteiligt, die ADO: das Überprüfen von Daten, das Untersuchen von Daten, das Bearbeiten und Aktualisieren von Daten verwenden. Diese Vorgänge werden im weiteren Verlauf dieses Abschnitts ausführlicher erläutert.  
  
 Bevor wir jedoch diese Details erörtern, werden wir uns eine Übersicht über das ADO-Objektmodell und eine einfache ADO-Anwendung vorstellen, die in Microsoft® Visual Basic® geschrieben wird und jeden der vier primären ADO-Vorgänge ausführt:  
  
-   [ADO-Objekte und -Collections](./ado-objects-and-collections.md)  
  
-   [HelloData: Eine einfache ADO-Anwendung](./hellodata-a-simple-ado-application.md)  
  
-   [OLE DB Anbieter](./ole-db-providers-ado.md)  
  
-   [Fehler](./errors-ado.md)