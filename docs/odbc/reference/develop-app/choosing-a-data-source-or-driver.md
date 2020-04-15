---
title: Auswählen einer Datenquelle oder eines Treibers | Microsoft Docs
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
ms.openlocfilehash: b10aafad95463f56ec0f5a029eac59a02cff003b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303371"
---
# <a name="choosing-a-data-source-or-driver"></a>Auswählen einer Datenquelle oder eines Treibers
Die Datenquelle oder der Treiber, die von einer Anwendung verwendet werden, ist manchmal in der Anwendung hartcodiert. Beispielsweise würde eine benutzerdefinierte Anwendung, die von einer MIS-Abteilung geschrieben wurde, um Daten von einer Datenquelle in eine andere zu übertragen, die Namen dieser Datenquellen enthalten - die Anwendung würde einfach nicht mit anderen Datenquellen funktionieren. Ein weiteres Beispiel ist eine vertikale Anwendung, z. B. eine, die für die Auftragserfassung verwendet wird. Eine solche Anwendung verwendet immer dieselbe Datenquelle, die über ein vordefiniertes Schema verfügt, das von der Anwendung bekannt ist.  
  
 Andere Anwendungen wählen die Datenquelle oder den Treiber zur Laufzeit aus. In der Regel handelt es sich dabei um generische Anwendungen, die Ad-hoc-Abfragen durchführen, z. B. eine Kalkulationstabelle, die ODBC zum Importieren von Daten verwendet. Solche Anwendungen listen in der Regel die verfügbaren Datenquellen oder Treiber auf und lassen Benutzer die Datenquellen auswählen, mit denen sie arbeiten möchten. Ob eine generische Anwendung Datenquellen, Treiber oder beides auflistet, hängt häufig davon ab, ob die Anwendung DBMS-basierte oder dateibasierte Treiber verwendet.  
  
 DBMS-basierte Treiber erfordern in der Regel einen komplexen Satz von Verbindungsinformationen, z. B. Netzwerkadresse, Netzwerkprotokoll, Datenbankname usw. Der Zweck einer Datenquelle besteht darin, alle diese Informationen auszublenden. Daher eignet sich das Datenquellenparadigma für die Verwendung mit DBMS-basierten Treibern. Eine Anwendung kann dem Benutzer auf zwei Arten eine Liste von Datenquellen anzeigen. Es kann **SQLDriverConnect** mit dem **DSN-Schlüsselwort** (Data Source Name) und ohne zugeordneten Wert aufrufen. Der Treiber-Manager zeigt eine Liste der Datenquellennamen an. Wenn die Anwendung die Darstellung der Liste steuern möchte, ruft sie **SQLDataSources** auf, um eine Liste der verfügbaren Datenquellen abzurufen, und erstellt ein eigenes Dialogfeld. Diese Funktion wird vom Treiber-Manager implementiert und kann aufgerufen werden, bevor Treiber geladen werden. Die Anwendung ruft dann eine Verbindungsfunktion auf und übergibt ihr den Namen der ausgewählten Datenquelle.  
  
 Wenn keine Datenquelle angegeben ist, wird die von den Systeminformationen angegebene Standarddatenquelle verwendet. (Weitere Informationen finden Sie unter [Standardunterschlüssel](../../../odbc/reference/install/default-subkey.md).) Wenn **SQLConnect** mit einem *ServerName-Argument* aufgerufen wird, das nicht gefunden werden kann, ein Nullzeiger ist oder "DEFAULT" ist, stellt der Treiber-Manager eine Verbindung mit der Standarddatenquelle her. Die Standarddatenquelle wird auch verwendet, wenn die Verbindungszeichenfolge, die bei einem Aufruf von **SQLDriverConnect** oder **SQLBrowseConnect** verwendet wird, das **Aufschlüsselwort DSN** auf "DEFAULT" enthält oder wenn die angegebene Datenquelle nicht gefunden wird. Darüber hinaus wird die Standarddatenquelle verwendet, wenn die Verbindungszeichenfolge, die in einem Aufruf von **SQLDriverConnect** verwendet wird, das **DSN-Schlüsselwort** nicht enthält.  
  
 Mit dateibasierten Treibern ist es möglich, ein Dateiparadigma zu verwenden. Bei Daten, die auf dem lokalen Computer gespeichert sind, wissen Benutzer häufig, dass sich ihre Daten in einer bestimmten Datei befinden, z. B. Employee.dbf. Anstatt eine unbekannte Datenquelle auszuwählen, ist es für diese Benutzer einfacher, die Datei auszuwählen, die sie kennen. Um dies zu implementieren, ruft die Anwendung zuerst **SQLDrivers auf.** Diese Funktion wird vom Treiber-Manager implementiert und kann aufgerufen werden, bevor Treiber geladen werden. **SQLDrivers** gibt eine Liste der verfügbaren Treiber zurück. Außerdem werden Werte für die Schlüsselwörter **FileUsage** und **FileExtns** zurückgegeben. Das **FileUsage-Schlüsselwort** erläutert, ob dateibasierte Treiber Dateien als Tabellen, wie Xbase oder als Datenbanken behandeln, ebenso wie Microsoft® Access. Das **FileExtns-Schlüsselwort** listet die Dateinamenerweiterungen auf, die der Treiber erkennt, z. B. .dbf für einen Xbase-Treiber. Anhand dieser Informationen erstellt die Anwendung ein Dialogfeld, über das der Benutzer eine Datei auswählt. Basierend auf der Erweiterung der ausgewählten Datei stellt die Anwendung dann eine Verbindung mit dem Treiber her, indem **sie SQLDriverConnect** mit dem **Schlüsselwort DRIVER** aufruft.  
  
 Es gibt nichts, was eine Anwendung daran hindert, eine Datenquelle mit einem dateibasierten Treiber zu verwenden oder **SQLDriverConnect** mit dem **Schlüsselwort DRIVER** aufzurufen, um eine Verbindung mit einem DBMS-basierten Treiber herzustellen. Hier sind mehrere häufige **DRIVER** Verwendungen des DRIVER-Schlüsselworts für DBMS-basierte Treiber:  
  
-   **Nicht das Erstellen von Datenquellen.** Eine benutzerdefinierte Anwendung kann z. B. einen bestimmten Treiber und eine bestimmte Datenbank verwenden. Wenn der Treibername und alle Informationen, die zum Herstellen einer Verbindung mit der Datenbank erforderlich sind, in der Anwendung hartcodiert sind, müssen Benutzer keine Datenquelle auf ihrem Computer erstellen, um die Anwendung auszuführen. Alles, was sie tun müssen, ist die Anwendung und den Treiber zu installieren.  
  
     Ein Nachteil dieser Methode besteht darin, dass die Anwendung neu kompiliert und neu verteilt werden muss, wenn sich die Verbindungsinformationen ändern. Wenn ein Datenquellenname in der Anwendung hartcodiert ist, anstatt vollständige Verbindungsinformationen zu erstellen, muss jeder Benutzer nur die Informationen in der Datenquelle ändern.  
  
-   **Zugriff auf ein bestimmtes DBMS ein einziges Mal.** Beispielsweise kann eine Kalkulationstabelle, die Daten durch Aufrufen von ODBC-Funktionen abruft, das **SCHLÜSSELwort DRIVER** enthalten, um einen bestimmten Treiber zu identifizieren. Da der Treibername für alle Benutzer, die über diesen Treiber verfügen, von Bedeutung ist, kann die Kalkulationstabelle an diese Benutzer übergeben werden. Wenn die Kalkulationstabelle einen Datenquellennamen enthält, muss jeder Benutzer dieselbe Datenquelle erstellen, um die Kalkulationstabelle zu verwenden.  
  
-   **Durchsuchen des Systems für alle Datenbanken, auf die ein bestimmter Treiber zugreifen kann.** Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md), weiter unten in diesem Abschnitt.
