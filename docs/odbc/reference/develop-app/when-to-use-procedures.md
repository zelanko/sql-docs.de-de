---
title: Verwendung von Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], procedures
- procedures [ODBC], about procedures
ms.assetid: 7dc9e327-dd54-4b10-9f66-9ef5c074f122
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 82e71e6849902eb2f02423560c534056112a139a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854518"
---
# <a name="when-to-use-procedures"></a>Verwendung von Prozeduren
Es gibt eine Reihe von Vorteilen, die mithilfe von Prozeduren, alle basiert auf der Tatsache, dass Prozeduren verschiebt SQL-Anweisungen von der Anwendung an die Datenquelle. Nun muss nur noch in der Anwendung ist ein interoperabler Prozeduraufruf. Diese Vorteile umfassen:  
  
-   **Leistung** Prozeduren sind in der Regel die schnellste Möglichkeit, SQL-Anweisungen ausführen. Wie vorbereitete Ausführung, die Anweisung wird kompiliert und in zwei separaten Schritte ausgeführt. Im Gegensatz zu vorbereitete Ausführung werden die Prozeduren nur zur Laufzeit ausgeführt. Zu einem anderen Zeitpunkt kompiliert werden.  
  
-   **Geschäftsregeln** ein *Geschäftsregel* ist eine Regel zu den Möglichkeiten, in dem ein Unternehmen Business verfügt. Beispielsweise kann nur eine Person mit dem Titel Vertriebsmitarbeiter können neue Aufträge hinzufügen. Platzieren diese Regeln in Prozeduren kann einzelne Unternehmen vertikale Anwendungen anpassen, indem Sie Neuerstellen der Prozeduren, die von der Anwendung aufgerufen werden, ohne den Anwendungscode ändern zu müssen. Auftragserfassungsanwendung kann z. B. die Prozedur aufrufen **InsertOrder** mit einer festen Anzahl von Parametern, wie genau **InsertOrder** wird implementiert, kann von Unternehmen zu Unternehmen variieren.  
  
-   **Replaceability** eng mit Platzieren von Geschäftsregeln in Prozeduren ist die Tatsache, dass Prozeduren ersetzt werden können, ohne die Anwendung erneut zu kompilieren. Wenn eine Geschäftsregel ändert, nachdem ein Unternehmen erworben haben und eine Anwendung installiert wurde, kann das Unternehmen die Prozedur, die mit dieser Regel ändern. Aus Sicht der Anwendung wurde nichts geändert Sie ruft immer noch eine bestimmte Prozedur um eine bestimmte Aufgabe durchzuführen.  
  
-   **DBMS-spezifische SQL** Prozeduren bieten eine Möglichkeit für die DBMS-spezifische SQL nutzen und weiterhin interoperablen Anwendungen. Beispielsweise kann eine Prozedur, auf ein DBMS, die ablaufsteuerung von Anweisungen in SQL unterstützt abfangen und Fehlern wiederherzustellen, während eine Prozedur auf ein DBMS, die ablaufsteuerung von Anweisungen nicht unterstützt einfach einen Fehler zurückgeben kann.  
  
-   **Prozeduren überstehen Transaktionen** für einige Datenquellen werden die Zugriffspläne für alle vorbereiteten Anweisungen für eine Verbindung gelöscht, wenn eine Transaktion ein Commit oder Rollback ist. Indem Sie ein SQL-Anweisungen in Prozeduren, die dauerhaft in der Datenquelle gespeichert werden, Überleben die Anweisungen die Transaktion. Angibt, ob die Prozeduren in mindestens eine vorbereitete, teilweise vorbereitet, überstehen eines Systemausfalls bzw. aufgehoben Zustand ist die DBMS-spezifische.  
  
-   **Trennen von Entwicklung** Prozeduren können getrennt vom Rest der Anwendung entwickelt werden. In großen Unternehmen gewährleistet dies eine Möglichkeit, die von Programmierern, sehr spezielle Fähigkeiten weiter zu nutzen. Das heißt, entwickeln Anwendungsprogrammierer Code der Benutzeroberfläche und Datenbankprogrammierer können Prozeduren schreiben.  
  
 Prozeduren werden in der Regel von vertikaler und benutzerdefinierten Anwendungen verwendet werden. Diese Anwendungen sind tendenziell feste Aufgaben ausführen, und es ist möglich, Programmieren Prozeduraufrufe darin. Auftragserfassungsanwendung kann z. B. die Prozeduren aufrufen **InsertOrder**, **DeleteOrder**, **UpdateOrder**, und **GetOrders** .  
  
 Es gibt keinen Grund zum Aufrufen von Prozeduren in generischen Anwendungen. Prozeduren werden normalerweise zum Ausführen einer Aufgabe im Kontext einer bestimmten Anwendung geschrieben, und haben daher keine Verwendung für allgemeine Anwendungen. Eine Tabelle hat beispielsweise keinen Grund, rufen Sie die **InsertOrder** gerade erwähnten Verfahren. Darüber hinaus sollten allgemeine Anwendungen keinen Verfahren zur Laufzeit zu bereitstellen schneller anweisungsausführung erstellen; ist nicht nur diesem wahrscheinlich langsamer als eine vorbereitete oder direkte Ausführung, es sind auch DBMS-spezifische SQL-Anweisungen erforderlich.  
  
 Eine Ausnahme ist die Anwendungsentwicklung-Umgebungen, die bieten häufig eine Möglichkeit für Programmierer, die SQL-Anweisungen zu erstellen, die Ausführen von Prozeduren und möglicherweise bieten eine Möglichkeit für Programmierer, die zum Testen von Prozeduren. Solche Umgebungen Aufruf **SQLProcedures** Liste verfügbaren Prozeduren und **SQLProcedureColumns** zum Auflisten der Eingabe, Input/Output und Output-Parameter der Prozedur zurückgegeben werden soll, Wert und die Spalten der keine Resultsets, die von einer Prozedur erstellt wird. Diese Prozeduren müssen jedoch im Voraus auf jede Datenquelle entwickelt werden; Dies ist also DBMS-spezifische SQL-Anweisungen erforderlich.  
  
 Es gibt drei wesentliche Nachteile der Verwendung von Prozeduren an. Die erste ist, dass Prozeduren geschrieben und für jede DBMS, mit denen die Anwendung ist die Ausführung, kompiliert werden müssen. Dies ist, zwar kein Problem für benutzerdefinierte Anwendungen können sie Entwicklungs- und Wartungszeiten für vertikale Anwendungen, die mit einer Reihe von DBMS-Systeme ausgeführt erheblich erhöhen.  
  
 Der zweite Nachteil ist, dass viele Datenbankmanagementsysteme Prozeduren nicht unterstützt werden. In diesem Fall ist dies wahrscheinlich ein Problem für vertikale Anwendungen, die mit einer Reihe von DBMS-Systeme ausgeführt werden. Um zu bestimmen, ob Prozeduren unterstützt werden, eine Anwendung ruft **SQLGetInfo** mit der Option SQL_PROCEDURES.  
  
 Der dritte Nachteil, der insbesondere für entwicklungsumgebungen für die Anwendung ist, ist, dass ODBC zum Erstellen von Prozeduren eine Grammatik für standard nicht definiert ist. D. h. Obwohl Anwendungen interoperably Prozeduren aufrufen können, können nicht sie diese interoperably erstellen.
