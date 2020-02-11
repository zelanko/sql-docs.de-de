---
title: Fenster 'Aufrufliste'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Call Stack Window [Transact-SQL]
ms.assetid: ddb0b19c-87cd-4883-bcb8-ec09ffb30369
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6707dc2e3c317c8b573eada62b2db07adbfa9d4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75243102"
---
# <a name="call-stack-window"></a>Fenster 'Aufrufliste'
  Im Fenster **Aufrufliste** werden die Module in der Aufrufliste angezeigt sowie die Datentypen und die Werte aller Parameter, die an die Module übergeben werden. [!INCLUDE[tsql](../../includes/tsql-md.md)] -Module umfassen gespeicherte Prozeduren, benutzerdefinierte Funktionen und Trigger. Um die Aufrufliste anzuzeigen, müssen Sie sich im Debugmodus befinden.  
  
## <a name="task-list"></a>Aufgabenliste  
 **So greifen Sie auf das Fenster Aufrufliste zu**  
  
-   Klicken Sie im Menü **Debuggen** auf **Fenster**und dann auf **Aufrufliste**.  
  
 **So ändern Sie den aktuellen Aufruflistenrahmen**  
  
 Sie können eine der folgenden Prozeduren verwenden, um einen Stapelrahmen zum aktuellen Rahmen zu machen:  
  
-   Klicken Sie mit der rechten Maustaste auf den Stapelrahmen, und klicken Sie dann auf **Zu Rahmen wechseln**.  
  
-   Doppelklicken Sie auf den Stapelrahmen.  
  
 **So zeigen Sie die Quelle eines anderen Rahmens an, der nicht der aktuelle Rahmen ist**  
  
-   Klicken Sie mit der rechten Maustaste auf den Stapelrahmen, und klicken Sie dann auf **Gehe zu Quellcode**.  
  
## <a name="stack-frames"></a>Stapelrahmen  
 Jede Zeile im Fenster **Aufrufliste** wird als Stapelrahmen bezeichnet und stellt entweder einen Aufruf aus einer [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skriptdatei zu einem Modul oder einen Aufruf von einem Modul zu einem anderen dar. Der untere Stapelrahmen im Anzeigebereich gibt die Zeile im [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor-Fenster an, die den ersten Aufruf an den Stapel ausgelöst hat. Die oberste Zeile gibt die Zeile an, an der der Debugger die Ausführung angehalten hat und die am linken Rand des Fensters durch einen gelben Pfeil gekennzeichnet ist. Jede dazwischen liegende Zeile gibt das Modul und die Zeilennummer des Quellcodes an, der den nächsthöheren Stapelrahmen aufgerufen hat.  
  
 Alle Ausdrücke in den Fenstern **Lokal**, **Überwachung**und **Schnellüberwachung** werden auf Grundlage des aktuellen Stapelrahmens ausgewertet. Im Abfrage-Editor-Fenster wird der Code für den aktuellen Rahmen angezeigt. Standardmäßig ist der aktuelle Stapelrahmen der Rahmen, in dem der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger die Ausführung angehalten hat. Wenn Sie den aktuellen Stapelrahmen zu einem anderen Rahmen ändern, werden die Ausdrücke in den Fenstern **Lokal**, **Überwachung**und **Schnellüberwachung** im Kontext des neuen Rahmens neu ausgewertet, und der Quellcode des neuen Rahmens wird im Abfrage-Editor-Fenster angezeigt.  
  
## <a name="columns"></a>Spalten  
 **Name**  
 Zeigt Informationen über ein Modul in der Aufrufliste an.  
  
 Für die letzte Zeile in der Aufrufliste werden unter **Name** das Abfrage-Editor-Quellcodefenster und die Zeilennummer des ersten Aufrufs an den Stapel aufgelistet. Für die anderen Zeilen hat **Name** das Format **Modul(Instanz.Datenbank)(Parameterliste) Zeilennummer**.  
  
 **Modul**  
 Der Name der gespeicherten Prozedur, Funktion oder gespeicherten Prozedur, die einen Aufruf zum nächsten Rahmen ausgelöst hat.  
  
 **Instanz.Datenbank**  
 Die Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] sowie die Datenbank, die das Modul enthält.  
  
 **Parameterliste**  
 Gibt für jeden Parameter, der während des Aufrufs an das Modul übergeben wird, den Datentyp, Namen und Wert an.  
  
 **LineNumber**  
 Für alle Zeilen mit Ausnahme der obersten gibt **Zeilennummer** an, welche Zeile im Modul einen Aufruf zum Rahmen ausgelöst hat. Für die oberste Zeile gibt **Zeilennummer** die Zeile an, auf die der Debugger gerade fokussiert ist.  
  
 **Sprache**  
 Zeigt **Transact-SQL** für [!INCLUDE[tsql](../../includes/tsql-md.md)]an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transact-SQL-Debugger](transact-sql-debugger.md)   
 [Transact-SQL-Debuggerinformationen](transact-sql-debugger-information.md)   
 [Schrittweises Durchlaufen von Transact-SQL-Code](step-through-transact-sql-code.md)  
