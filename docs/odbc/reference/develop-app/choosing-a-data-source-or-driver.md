---
description: Auswählen einer Datenquelle oder eines Treibers
title: Auswählen einer Datenquelle oder eines Treibers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], selecting driver
- connecting to data source [ODBC], selecting data source
- data sources [ODBC], selecting
- ODBC drivers [ODBC], selecting
ms.assetid: 10aaf570-01ab-4478-8339-bdde2a5e3dd1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 215e249fe354396239118394d4e792ced67bc82d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461602"
---
# <a name="choosing-a-data-source-or-driver"></a>Auswählen einer Datenquelle oder eines Treibers
Die von einer Anwendung verwendete Datenquelle oder der Treiber ist in der Anwendung manchmal hart codiert. Beispielsweise würde eine benutzerdefinierte Anwendung, die von einer missabteilung geschrieben wurde, um Daten aus einer Datenquelle in eine andere zu übertragen, die Namen dieser Datenquellen enthalten. die Anwendung funktioniert einfach nicht mit anderen Datenquellen. Ein weiteres Beispiel ist eine vertikale Anwendung, z. b. eine, die für den Bestell Eintrag verwendet wird. Eine solche Anwendung verwendet immer dieselbe Datenquelle, die über ein vordefiniertes Schema verfügt, das von der Anwendung bekannt ist.  
  
 Andere Anwendungen wählen die Datenquelle oder den Treiber zur Laufzeit aus. Normalerweise handelt es sich hierbei um generische Anwendungen, die Ad-hoc-Abfragen durchführen, z. b. eine Tabelle, die ODBC zum Importieren von Daten Solche Anwendungen Listen normalerweise die verfügbaren Datenquellen oder Treiber auf und ermöglichen Benutzern die Auswahl derjenigen, mit denen Sie arbeiten möchten. Ob eine generische Anwendung Datenquellen, Treiber oder beides häufig auflistet, hängt davon ab, ob die Anwendung DBMS-basierte oder dateibasierte Treiber verwendet.  
  
 Bei DBMS-basierten Treibern benötigen Sie in der Regel einen komplexen Satz von Verbindungsinformationen, wie z. b. die Netzwerkadresse, das Netzwerkprotokoll, den Datenbanknamen usw. Der Zweck einer Datenquelle besteht darin, alle diese Informationen auszublenden. Daher eignet sich das Datenquellen Paradigma für die Verwendung mit DBMS-basierten Treibern. Eine Anwendung kann dem Benutzer eine Liste von Datenquellen auf zwei Arten anzeigen. Es kann **SQLDriverConnect** mit dem **DSN** -Schlüsselwort (Datenquellen Name) und ohne zugeordneten Wert aufgerufen werden. der Treiber-Manager zeigt eine Liste der Datenquellen Namen an. Wenn die Anwendung die Kontrolle über die Darstellung der Liste will, ruft Sie **SQLDataSources** auf, um eine Liste der verfügbaren Datenquellen abzurufen und ein eigenes Dialogfeld zu konstruieren. Diese Funktion wird vom Treiber-Manager implementiert und kann aufgerufen werden, bevor Treiber geladen werden. Die Anwendung ruft dann eine Verbindungsfunktion auf und übergibt ihr den Namen der ausgewählten Datenquelle.  
  
 Wenn keine Datenquelle angegeben ist, wird die von den Systeminformationen angegebene Standarddaten Quelle verwendet. (Weitere Informationen finden Sie unter [Standard Unterschlüssel](../../../odbc/reference/install/default-subkey.md).) Wenn **SQLCONNECT** mit einem *Servername* -Argument aufgerufen wird, das nicht gefunden werden kann, ein NULL-Zeiger ist oder "Default" ist, stellt der Treiber-Manager eine Verbindung mit der Standarddaten Quelle her. Die Standarddaten Quelle wird auch verwendet, wenn die Verbindungs Zeichenfolge, die in einem **SQLDriverConnect** -oder **sqlbrowseconnetct** -Befehl verwendet wird, das **DSN** -Schlüsselwort enthält, das auf "Default" festgelegt ist, oder wenn die angegebene Datenquelle nicht gefunden wurde. Außerdem wird die Standarddaten Quelle verwendet, wenn die Verbindungs Zeichenfolge, die in einem-Befehl von **SQLDriverConnect** verwendet wird, das **DSN** -Schlüsselwort nicht enthält.  
  
 Bei dateibasierten Treibern ist es möglich, ein Datei Paradigma zu verwenden. Für Daten, die auf dem lokalen Computer gespeichert sind, wissen Benutzer häufig, dass Ihre Daten in einer bestimmten Datei enthalten sind, z. b. Employee. DBF. Anstatt eine unbekannte Datenquelle auszuwählen, ist es für solche Benutzer einfacher, die Datei auszuwählen, die Sie kennen. Um dies zu implementieren, ruft die Anwendung zuerst **SQLDrivers**auf. Diese Funktion wird vom Treiber-Manager implementiert und kann aufgerufen werden, bevor Treiber geladen werden. **SQLDrivers** gibt eine Liste der verfügbaren Treiber zurück. Außerdem werden Werte für die Schlüsselwörter " **fileusage** " und " **fileextns** " zurückgegeben. Das **fileusage** -Schlüsselwort erläutert, ob dateibasierte Treiberdateien als Tabellen wie xbase oder AS-Datenbanken behandeln, ebenso wie von Microsoft®. Das **fileextns** -Schlüsselwort listet die Dateinamen Erweiterungen auf, die der Treiber erkennt, z. b.. dbf für einen xbase-Treiber. Mithilfe dieser Informationen erstellt die Anwendung ein Dialogfeld, über das der Benutzer eine Datei auswählt. Basierend auf der Erweiterung der ausgewählten Datei stellt die Anwendung eine Verbindung mit dem Treiber her, indem **SQLDriverConnect** mit dem **Treiber** Schlüsselwort aufgerufen wird.  
  
 Es ist nicht zu verhindern, dass eine Anwendung eine Datenquelle mit einem dateibasierten Treiber verwendet oder **SQLDriverConnect** mit dem **Treiber** Schlüsselwort aufruft, um eine Verbindung mit einem DBMS-basierten Treiber herzustellen. Im folgenden finden Sie einige häufige Verwendungsmöglichkeiten für das **Treiber** Schlüsselwort für DBMS-basierte Treiber:  
  
-   **Keine Datenquellen werden erstellt.** Beispielsweise kann eine benutzerdefinierte Anwendung einen bestimmten Treiber und eine bestimmte Datenbank verwenden. Wenn der Treiber Name und alle Informationen, die zum Herstellen einer Verbindung mit der Datenbank erforderlich sind, in der Anwendung hart codiert sind, müssen die Benutzer auf Ihrem Computer keine Datenquelle erstellen, um die Anwendung auszuführen. Sie müssen lediglich die Anwendung und den Treiber installieren.  
  
     Ein Nachteil dieser Methode besteht darin, dass die Anwendung neu kompiliert und verteilt werden muss, wenn sich die Verbindungsinformationen ändern. Wenn ein Datenquellen Name in der Anwendung hart codiert ist, anstatt die Verbindungsinformationen abzuschließen, muss jeder Benutzer nur die Informationen in der Datenquelle ändern.  
  
-   **Das einmalige zugreifen auf ein bestimmtes DBMS.** Beispielsweise kann eine Kalkulations Tabelle, die Daten durch Aufrufen von ODBC-Funktionen abruft, das **Treiber** Schlüsselwort enthalten, um einen bestimmten Treiber zu identifizieren. Da der Treiber Name für Benutzer, die über diesen Treiber verfügen, aussagekräftig ist, kann die Tabelle an diese Benutzer übermittelt werden. Wenn die Tabelle einen Datenquellen Namen enthielt, muss jeder Benutzer die gleiche Datenquelle für die Verwendung des Arbeitsblatts erstellen.  
  
-   **Durchsuchen des Systems für alle Datenbanken, auf die ein bestimmter Treiber zugreifen kann.** Weitere Informationen finden Sie weiter unten in diesem Abschnitt unter [Herstellen einer Verbindung mit sqlbrowseconnetct](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md).
