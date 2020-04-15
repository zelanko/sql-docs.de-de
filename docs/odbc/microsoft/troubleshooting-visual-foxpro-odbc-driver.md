---
title: Fehlerbehebung (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
ms.openlocfilehash: 70b035069c0be88d05a3aa5e17b96af991c27405
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303031"
---
# <a name="troubleshooting-visual-foxpro-odbc-driver"></a>Problembehandlung (Visual FoxPro-ODBC-Treiber)
In den folgenden Abschnitten wird erläutert, wie Sie die Leistung verbessern und Probleme lösen können, die bei der Verwendung des Visual FoxPro ODBC-Treibers auftreten können.  
  
## <a name="accessing-parameterized-views"></a>Zugreifen auf parametrisierte Ansichten  
 Sie können mit dem Treiber nicht auf parametrisierte Ansichten in einer Visual FoxPro-Datenbank zugreifen. Eine parametrisierte Ansicht erstellt eine WHERE-Klausel in der SQL **SELECT-Anweisung** der Ansicht, die die heruntergeladenen Datensätze auf die Datensätze beschränkt, die die Bedingungen der WHERE-Klausel erfüllen, die mit dem für den Parameter angegebenen Wert erstellt wurde. Da der Treiber das Übergeben von Parametern an die Ansicht nicht unterstützt, schlägt der Versuch fehl, mithilfe des Treibers auf eine parametrisierte Ansicht zuzugreifen.  
  
 Der Parameterwert kann zur Laufzeit angegeben oder programmgesteuert an die Ansicht übergeben werden.  
  
## <a name="accessing-remote-views"></a>Zugriff auf Remoteansichten  
 Mit dem Treiber können Sie nicht auf Remoteansichten in einer Visual FoxPro-Datenbank zugreifen. Remoteansichten sind Ansichten, die entweder auf Nicht-FoxPro-Daten oder eine Kombination aus FoxPro- und Nicht-FoxPro-Daten zugreifen. Verwenden Sie Visual FoxPro, um auf Remoteansichten zuzugreifen.  
  
## <a name="deleting-records"></a>Löschen von Datensätzen  
 Sie können Datensätze zum Löschen mit dem Treiber markieren, aber Sie können Datensätze nicht dauerhaft aus der Datenbank entfernen. Um Datensätze dauerhaft aus einer Tabelle zu entfernen, verwenden Sie Visual FoxPro.  
  
## <a name="increasing-performance-using-background-fetching"></a>Erhöhen der Leistung mithilfe des Abrufens von Hintergründen  
 Sie können die Leistung bei großen Abrufungen verbessern, indem Sie die Hintergrund-Abruffunktion des Treibers verwenden. Beim Abrufen von Hintergründen wird ein separater Thread verwendet, um Daten abzurufen, die von einer bestimmten Datenquelle angefordert wurden.  
  
 Sie können das Abrufen von Hintergrunddaten für eine Datenquelle auf eine der folgenden Arten verwenden:  
  
-   Aktivieren Sie das Kontrollkästchen **Daten im Hintergrund** im [Dialogfeld ODBC Visual FoxPro Setup](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)abrufen .  
  
-   Verwenden Sie das Schlüsselwort BackgroundFetch-Attribut in ihrer Verbindungszeichenfolge.  
  
 Informationen zu Schlüsselwörtern für Verbindungszeichenfolgenattribute finden Sie unter [Verwenden von Verbindungszeichenfolgen](../../odbc/microsoft/using-connection-strings.md).  
  
## <a name="updating-multitiered-views"></a>Aktualisieren von mehrstufigen Ansichten  
 Eine mehrstufige Ansicht ist eine Ansicht, die auf einer oder mehreren Ansichten und nicht auf einer Basistabelle basiert. Wenn Sie Daten in einer mehrstufigen Ansicht aktualisieren, gehen die Aktualisierungen nur eine Ebene nach unten, auf die Ansicht, auf der die Ansicht der obersten Ebene basiert. Basistabellen werden nicht aktualisiert.  
  
## <a name="using-data-definition-language-ddl-in-stored-procedures"></a>Verwenden von Datendefinitionssprache (Data Definition Language, DDL) in gespeicherten Prozeduren  
 Sie können DDL, z. B. CREATE TABLE oder ALTER TABLE, in gespeicherten Visual FoxPro-Prozeduren nicht verwenden.  
  
 Informationen zur Sprache, die Sie in gespeicherten Prozeduren verwenden können, finden Sie unter [Support für Regeln, Trigger, Standardwerte und gespeicherte Prozeduren](../../odbc/microsoft/support-rules-triggers-defaults-stored-procedures-visual-foxpro-odbc-driver.md).  
  
## <a name="using-positioned-updates"></a>Verwenden von positionierten Updates  
 Der Treiber unterstützt keine positionierten Updates. Verwenden Sie die SQL WHERE-Klausel, um die Zeilen zu identifizieren, die Sie aktualisieren möchten.  
  
## <a name="using-the-set-ansi-command"></a>Verwenden des SET ANSI-Befehls  
 Wenn Sie ein Visual FoxPro-Entwickler sind, sollten Sie sich bewusst sein, dass die Standardeinstellung für SET ANSI für den Treiber aktiviert ist, im Gegensatz zu einer Standardeinstellung von OFF für Visual FoxPro. Die Standardeinstellung ON für SET ANSI ermöglicht Visual FoxPro-Datenquellen ein konsistentes Verhalten mit anderen ODBC-Datenquellen, die in der Regel genaue Vergleiche durchführen. Sie können die Standardeinstellung ändern. Weitere Informationen finden Sie unter [SET ANSI](../../odbc/microsoft/set-ansi-command.md).
