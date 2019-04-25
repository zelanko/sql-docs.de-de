---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f0576d017068b8ab0694da798c5be458f115e56
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62632606"
---
# <a name="troubleshooting-visual-foxpro-odbc-driver"></a>Problembehandlung (Visual FoxPro-ODBC-Treiber)
In den folgenden Abschnitten erläutert die Leistung verbessern, und lösen Sie Probleme, die möglicherweise auftreten, bei der Verwendung des Visual FoxPro-ODBC-Treibers.  
  
## <a name="accessing-parameterized-views"></a>Zugreifen auf parametrisierten Ansichten  
 Sie können keine parametrisierte Sichten in einer Visual FoxPro-Datenbank, die mit dem Treiber zugreifen. Eine parametrisierte Sicht erstellt eine WHERE-Klausel in der Ansicht SQL **wählen** -Anweisung, die die Datensätze beschränkt, die auf die Datensätze, die die Bedingungen der WHERE-Klausel angegebene Wert für den Parameter mit erstellt erfüllen heruntergeladen. Da der Treiber keine übergeben von Parametern an die Ansicht unterstützt, schlagen Versuche für eine parametrisierte Ansicht mit dem Treiber fehl.  
  
 Der Wert des Parameters zur Laufzeit oder programmgesteuert an die Ansicht übergeben werden.  
  
## <a name="accessing-remote-views"></a>Zugreifen auf Remote-Ansichten  
 Sie können nicht remote Sichten in einer Visual FoxPro-Datenbank, die mit dem Treiber zugreifen. Remote-Ansichten sind Ansichten, die entweder nicht FoxPro-Daten oder eine Kombination von FoxPro und nicht-FoxPro-Daten zugreifen. Verwenden Sie für den Zugriff auf remote-Ansichten, Visual FoxPro.  
  
## <a name="deleting-records"></a>Löschen von Datensätzen  
 Sie können die Einträge zum Löschen, die mit dem Treiber markieren, aber keine Datensätze dauerhaft aus der Datenbank entfernt. Verwenden Sie Visual FoxPro, um Einträge dauerhaft aus einer Tabelle zu entfernen.  
  
## <a name="increasing-performance-using-background-fetching"></a>Erhöhen der Leistung mithilfe der Hintergrund abrufen  
 Sie können die Leistung in großen Abrufvorgängen verbessern, indem Sie mithilfe der Funktion des Treibers abrufen im Hintergrund. Abrufen der Hintergrund verwendet einen eigenen Thread zum Abrufen von Daten aus einer bestimmten Datenquelle angefordert.  
  
 Sie nutzen, Hintergrund, die für eine Datenquelle in einem der folgenden Arten abgerufen werden können:  
  
-   Überprüfen Sie die **rufen Sie Daten im Hintergrund** aktivieren Sie das Kontrollkästchen der [Dialogfeld ODBC-Visual FoxPro-Setup](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md).  
  
-   Verwenden Sie das Schlüsselwort der BackgroundFetch-Attribut, in der Verbindungszeichenfolge.  
  
 Weitere Informationen zu Schlüsselwörtern für Verbindungszeichenfolgen-Attribut, finden Sie unter [Verbindungszeichenfolgen verwenden](../../odbc/microsoft/using-connection-strings.md).  
  
## <a name="updating-multitiered-views"></a>Aktualisieren von Sichten mit mehreren Ebenen  
 Eine Ansicht von mehreren Ebenen ist eine Ansicht basierend auf einer oder mehreren Ansichten und nicht auf eine Basistabelle. Wenn Sie Daten in einer mehrstufigen Ansicht aktualisieren, wechseln die Updates nur eine Ebene tiefer, an die Ansicht, die auf der die Ansicht der obersten Ebene basiert; Basistabellen werden nicht aktualisiert werden.  
  
## <a name="using-data-definition-language-ddl-in-stored-procedures"></a>Mithilfe der Datendefinitionssprache (DDL) in gespeicherten Prozeduren  
 DDL-Trigger, z. B. CREATE TABLE oder ALTER TABLE, können keine in Visual FoxPro-gespeicherten Prozeduren.  
  
 Weitere Informationen zur Sprache, die Sie in gespeicherten Prozeduren verwenden können, finden Sie unter [Unterstützung für Regeln, Trigger, Standardwerte und gespeicherte Prozeduren](../../odbc/microsoft/support-rules-triggers-defaults-stored-procedures-visual-foxpro-odbc-driver.md).  
  
## <a name="using-positioned-updates"></a>Positionierte Updates verwenden  
 Der Treiber unterstützt keine positionierten Updates. Verwenden Sie die SQL-WHERE-Klausel, um die Zeilen zu identifizieren, die Sie aktualisieren möchten.  
  
## <a name="using-the-set-ansi-command"></a>Verwenden den Befehl SET ANSI  
 Wenn Sie eine Visual FoxPro-Entwickler sind, sollte Sie bewusst sein, dass die Standardeinstellung für SET ANSI ON im Gegensatz zum einer Standardeinstellung OFF für Visual FoxPro-Treiber ist. Der Standardwert für die Einstellung für SET ANSI ermöglicht Visual FoxPro-Datenquellen für andere ODBC-Datenquellen konsistentes Verhalten, die in der Regel genau Vergleiche ausführen. Sie können die Standardeinstellung ändern. Weitere Informationen finden Sie unter [SET ANSI](../../odbc/microsoft/set-ansi-command.md).
