---
description: Problembehandlung (Visual FoxPro-ODBC-Treiber)
title: Problembehandlung (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set ANSI [ODBC]
- troubleshooting Visual FoxPro ODBC driver [ODBC]
- remote views [ODBC]
- multitiered views [ODBC]
- parameterized views [ODBC], Visual FoxPro ODBC driver
- fetches [ODBC], Visual FoxPro ODBC driver
- positioned updates [ODBC]
- background fetching [ODBC]
ms.assetid: fd478dd8-666a-4f0a-a2d6-b94e81cbbe4b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 73f98f66a09b0ff17987186103b38643047f1762
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471433"
---
# <a name="troubleshooting-visual-foxpro-odbc-driver"></a>Problembehandlung (Visual FoxPro-ODBC-Treiber)
In den folgenden Abschnitten wird erläutert, wie die Leistung verbessert und Probleme gelöst werden, die bei der Verwendung des Visual FoxPro-ODBC-Treibers auftreten können.  
  
## <a name="accessing-parameterized-views"></a>Zugreifen auf parametrisierte Sichten  
 Der Zugriff auf parametrisierte Sichten in einer Visual FoxPro-Datenbank ist mit dem Treiber nicht möglich. In einer parametrisierten Sicht wird eine WHERE-Klausel in der SQL- **Select** -Anweisung der Sicht erstellt, die die Datensätze einschränkt, die auf die Datensätze heruntergeladen werden, die die Bedingungen der WHERE-Klausel erfüllen, die mit dem für den Parameter angegebenen Wert Da der Treiber das Übergeben von Parametern an die Sicht nicht unterstützt, tritt beim Versuch, auf eine parametrisierte Ansicht mithilfe des Treibers zuzugreifen, ein Fehler auf.  
  
 Der Parameterwert kann zur Laufzeit bereitgestellt oder Programm gesteuert an die Ansicht übergeben werden.  
  
## <a name="accessing-remote-views"></a>Zugreifen auf Remote Sichten  
 Sie können mit dem Treiber nicht auf Remote Sichten in einer Visual FoxPro-Datenbank zugreifen. Remote Sichten sind Sichten, die entweder auf nicht-FoxPro-Daten oder eine Kombination aus FoxPro-und nicht-FoxPro-Daten zugreifen. Verwenden Sie Visual FoxPro, um auf Remote Ansichten zuzugreifen.  
  
## <a name="deleting-records"></a>Löschen von Datensätzen  
 Sie können Datensätze zum Löschen mithilfe des Treibers markieren, aber Sie können Datensätze nicht endgültig aus der Datenbank entfernen. Verwenden Sie Visual FoxPro, um Datensätze dauerhaft aus einer Tabelle zu entfernen.  
  
## <a name="increasing-performance-using-background-fetching"></a>Erhöhen der Leistung mithilfe des Hintergrunds für das Abrufen  
 Sie können die Leistung bei umfangreichen Abruf Vorgängen verbessern, indem Sie das Feature für das Hintergrund Abrufen des Treibers verwenden. Beim Abrufen des Hintergrunds wird ein separater Thread verwendet, um die von einer bestimmten Datenquelle angeforderten Daten abzurufen.  
  
 Sie können das Abrufen von Hintergrunddaten für eine Datenquelle auf eine der folgenden Weisen anwenden:  
  
-   Aktivieren Sie das Kontrollkästchen **Daten im Hintergrund abrufen** im [Dialogfeld Visual FoxPro-Setup von ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md).  
  
-   Verwenden Sie das backgroundfetch-Attribut Schlüsselwort in der Verbindungs Zeichenfolge.  
  
 Informationen zu Schlüsselwörtern für Verbindungs Zeichenfolgen-Attribute finden [Sie unter Verwenden von Verbindungs](../../odbc/microsoft/using-connection-strings.md)Zeichen  
  
## <a name="updating-multitiered-views"></a>Aktualisieren von mehrstufigen Sichten  
 Eine mehrstufige Ansicht ist eine Ansicht, die auf einer oder mehreren Ansichten statt auf einer Basistabelle basiert. Wenn Sie Daten in einer mehrstufigen Ansicht aktualisieren, werden die Updates nur eine Ebene nach unten verschoben, um die Ansicht anzuzeigen, auf der die Ansicht der obersten Ebene basiert. Basistabellen werden nicht aktualisiert.  
  
## <a name="using-data-definition-language-ddl-in-stored-procedures"></a>Verwenden von DDL (Data Definition Language) in gespeicherten Prozeduren  
 DDL (z. b. CREATE TABLE oder ALTER TABLE) kann nicht in gespeicherten Prozeduren von Visual FoxPro verwendet werden.  
  
 Informationen zu der Sprache, die Sie in gespeicherten Prozeduren verwenden können, finden Sie [unter Unterstützung für Regeln, Trigger, Standardwerte und gespeicherte Prozeduren](../../odbc/microsoft/support-rules-triggers-defaults-stored-procedures-visual-foxpro-odbc-driver.md).  
  
## <a name="using-positioned-updates"></a>Verwenden positionierter Updates  
 Positionierte Updates werden vom Treiber nicht unterstützt. Verwenden Sie die SQL-WHERE-Klausel, um die Zeilen zu identifizieren, die Sie aktualisieren möchten.  
  
## <a name="using-the-set-ansi-command"></a>Verwenden des Befehls "SET ANSI"  
 Wenn Sie Visual FoxPro-Entwickler sind, sollten Sie beachten, dass die Standardeinstellung für SET ANSI für den Treiber auf ON festgelegt ist, im Gegensatz zur Standardeinstellung Off für Visual FoxPro. Mit der Standardeinstellung für SET ANSI können sich Visual FoxPro-Datenquellen konsistent mit anderen ODBC-Datenquellen Verhalten, die in der Regel exakte Vergleiche ausführen. Sie können die Standardeinstellung ändern. Weitere Informationen finden Sie unter [SET ANSI](../../odbc/microsoft/set-ansi-command.md).
