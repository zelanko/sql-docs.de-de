---
title: Verwendungs Szenarien und Beispiele für die CLR-Integration (Common Language Runtime) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- scenarios [CLR integration]
- common language runtime [SQL Server], samples
- examples [CLR integration]
- sample applications [CLR integration]
- database objects [CLR integration], samples
- managed code [SQL Server], samples
ms.assetid: 33aac25f-abb4-4f29-af88-4a0dacd80ae7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 30a54064d398ec6db09a9ccd54eed9411a7f905a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933212"
---
# <a name="usage-scenarios-and-examples-for-common-language-runtime-clr-integration"></a>Verwendungsszenarien und Beispiele für Common Language Runtime (CLR)-Integration
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält Beispielanwendungen, Paketbeispiele und zahlreiche Codebeispiele, die Sie zum Erlernen der CLR (Common Language Runtime)-Programmierbarkeitsfunktionen verwenden können.  
  
 Umfassende Visual Studio-Projekte, die diese Beispiele und zusätzlichen Materialien implementieren, finden Sie unter [Microsoft SQL Server Community Projects & Beispiele auf CodePlex](https://go.microsoft.com/fwlink/?LinkID=193935).  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[Zugreifen auf systemeigenen Code von einer CLR-UDF](../../../2014/database-engine/dev-guide/accessing-native-code-from-a-clr-udf.md)|Zeigt, wie eine Funktion in systemeigenem (nicht verwaltetem) C++-Code in der Datenbank von einer benutzerdefinierten Funktion in einer Assembly aufgerufen wird.|  
|[Beispiel für einen Arrayparameter](../../../2014/database-engine/dev-guide/array-parameter-sample.md)|Zeigt, wie Sie eine Gruppe von Zeilen in einer Datenbank durch Übergeben eines Arrays mit Informationen von einem Client an eine CLR-gespeicherte Prozedur auf dem Server erstellen, aktualisieren oder löschen können. Zu diesem Zweck wird ein UDT verwendet.|  
|[Beispiel für das Kalender-/Uhrzeit-UDT](../../../2014/database-engine/dev-guide/calendar-aware-date-and-time-udt-sample.md)|Definiert zwei UDTs, die die dem lokal gültigen Kalender entsprechende Verarbeitung von Daten und Uhrzeiten bereitstellen.|  
|[Beispiel für CLR-Transaktionen](../../../2014/database-engine/dev-guide/clr-transactions-sample.md)|Veranschaulicht das Steuern von Transaktionen mithilfe der im System.Transactions-Namespace vorhandenen verwalteten APIs.|  
|[Erstellung von Kontakten mit CLR und XML](../../../2014/database-engine/dev-guide/contact-creation-using-clr-and-xml.md)|Das Kontakterstellungsbeispiel für SQL Server stellt nützliche Hilfsprogramme bereit, die eine zusätzliche Funktionalitätsebene auf der einfachen AdventureWorks2012-Beispieldatenbank bilden. Das erste Hilfsprogramm erstellt Kontaktdatensätze für die verschiedenen Personen, die mit der AdventureWorks2012-Datenbank in Verbindung stehen. Die Kontaktinformationen werden mit XML angegeben und an eine C#- oder VB-basierte gespeicherte Prozedur übergeben, um das XML zu erstellen und es in die ordnungsgemäßen Tabellen für die Datenbank einzufügen.|  
|[Currency-Typ und Konvertierungsfunktion](../../../2014/database-engine/dev-guide/currency-type-and-conversion-function.md)|Definiert einen benutzerdefinierten Currency-Datentyp mithilfe von C#.|  
|[Behandeln von großen Objekten mit CLR](../../../2014/database-engine/dev-guide/handling-large-objects-using-clr.md)|Veranschaulicht die Übertragung großer Binär Objekte (LOB) zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und einem Dateisystem, auf das der Server mit gespeicherten CLR-Prozeduren zugreifen kann.|  
|[Beispiel für "Hello World Ready"](../../../2014/database-engine/dev-guide/hello-world-ready-sample.md)|Veranschaulicht die grundlegenden Vorgänge, die beim Erstellen, Bereitstellen und Testen einer einfachen gespeicherten World-Ready-Prozedur, die auf der CLR-Integration basiert, ausgeführt werden müssen.|  
|[„Hello World“-Beispiel](../../../2014/database-engine/dev-guide/hello-world-sample.md)|Veranschaulicht die grundlegenden Vorgänge zum Erstellen, bereitstellen und Testen einer einfachen CLR-Integrations basierten gespeicherten Prozedur.|  
|[Beispiel für In-Process-Datenzugriff](../../../2014/database-engine/dev-guide/in-process-data-access-sample.md)|Enthält eine bestimmte Anzahl von einfachen Funktionen zur Demonstration verschiedener Funktionen des prozessinternen CLR-Datenzugriffsanbieters.|  
|[Beispiel für einen Ergebnissatz](../../../2014/database-engine/dev-guide/result-set-sample.md)|Veranschaulicht, wie Befehle beim Durchsehen der Ergebnisse einer Abfrage ausgeführt werden können, ohne eine neue Verbindung öffnen und ohne alle Ergebnisse in den Speicher laden zu müssen.|  
|[Beispiel für das Senden eines Datensatzes](../../../2014/database-engine/dev-guide/send-dataset-sample.md)|Zeigt, wie Sie ein auf ADO.NET basiertes Dataset in einer serverseitigen CLR-basierten gespeicherten Prozedur als Resultset an den Client zurückgeben.|  
|[Beispiel für Zeichenfolgenhilfsprogramm-Funktionen](../../../2014/database-engine/dev-guide/string-utility-functions-sample.md)|Enthält eine Streaming-Tabellenwertfunktion (Table-Valued Function, TVF) in Visual C# und Visual Basic, die eine durch Trennzeichen getrennte Zeichenfolge in eine Tabelle mit einer Spalte unterteilt.|  
|[Beispiel für Zeichenfolgendarstellung mit ergänzenden Zeichen](../../../2014/database-engine/dev-guide/supplementary-aware-string-manipulation-sample.md)|Zeigt die Implementierung von fünf [!INCLUDE[tsql](../../includes/tsql-md.md)]-Zeichenfolgenfunktionen mit ergänzenden Funktionen, die sowohl Unicode- als auch Ersatzzeichenfolgen verarbeiten können.|  
|[UDT-Hilfsprogramme](../../../2014/database-engine/dev-guide/udt-utilities.md)|Enthält eine Reihe von Hilfsprogrammfunktionen mit benutzerdefiniertem Datentyp (User-Defined Data Type, UDT).|  
|[Bereinigung nicht verwendeter Assemblys](../../../2014/database-engine/dev-guide/unused-assembly-cleanup.md)|Enthält eine gespeicherte .NET-Prozedur, die durch Abfragen der Metadaten-Kataloge nicht verwendete Assemblys in der aktuellen Datenbank löscht.|  
|[Benutzerdefinierter Typ](../../../2014/database-engine/dev-guide/user-defined-type.md)|Veranschaulicht das Erstellen und Verwenden eines einfachen UDT sowohl aus [!INCLUDE[tsql](../../includes/tsql-md.md)] als auch aus einer Clientanwendung heraus, die System.Data.SqlClient verwendet.|  
|[UTF8 String, benutzerdefinierter Datentyp &#40;UDT&#41;](../../../2014/database-engine/dev-guide/utf8-string-user-defined-data-type-udt.md)|Veranschaulicht die Implementierung eines UDT, der das Typensystem der Datenbank erweitert, um UTF8-codierte Werte speichern zu können.|  
  
  
