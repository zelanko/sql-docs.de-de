---
title: Auswählen einer Datenquelle oder einem Treiber | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c238b89f6fefbb158c50531d28d2c234c64f64bf
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52507626"
---
# <a name="choosing-a-data-source-or-driver"></a>Auswählen einer Datenquelle oder eines Treibers
Die Datenquelle oder von einer Anwendung verwendeten Treiber ist manchmal in der Anwendung hartcodiert. Z. B. eine benutzerdefinierte Anwendung geschrieben von der Abteilung MIS zum Übertragen von Daten aus einer Datenquelle in eine andere enthält die Namen dieser Daten Quellen: die Anwendung einfach funktioniert nicht mit allen anderen Datenquellen. Ein weiteres Beispiel ist eine vertikale Anwendung verwendet werden, z. B. für Bestellungen eingeben. Eine solche Anwendung immer verwendet die gleiche Datenquelle, mit einem vordefinierten Schema, das von der Anwendung bezeichnet.  
  
 Andere Anwendungen wählen Sie die Datenquelle oder Treiber zur Laufzeit. In der Regel sind dies allgemeiner Anwendungen, die ad-hoc-Abfragen, z. B. eine Tabelle, die ODBC verwendet, um Daten zu importieren. Solche Anwendungen in der Regel Auflisten der verfügbaren Datenquellen oder Treiber und können Benutzer die Produkte auszuwählen, die, denen Sie verwenden möchten. Gibt an, ob eine generische Anwendung Datenquellen, Treiber oder beides häufig enthält, hängt davon ab, ob die Anwendung die DBMS-basierten oder dateibasierte Treiber verwendet.  
  
 DBMS-basierten Treibern erfordern in der Regel einen komplexen Satz von Verbindungsinformationen, z. B. die Netzwerkadresse, Netzwerkprotokoll, Datenbankname, usw. an. Der Zweck einer Datenquelle ist So blenden Sie alle diese Informationen aus. Aus diesem Grund ist das Data-Source-Paradigma für die Verwendung mit DBMS-basierten Treibern. Eine Anwendung kann eine Liste der Datenquellen für den Benutzer auf zwei Arten anzeigen. Aufrufen **SQLDriverConnect** mit der **DSN** (Data Source Name)-Schlüsselwort und keinen zugeordneten Wert, der Treiber-Manager zeigt eine Liste der Datenquellennamen. Wenn die Steuerung der Darstellung der Liste der von der Anwendung versucht wird, ruft es **SQLDataSources** zum Abrufen einer Liste verfügbarer Datenquellen und ein eigenes Dialogfeld erstellt. Diese Funktion wird vom Treiber-Manager implementiert und kann aufgerufen werden, bevor alle Treiber geladen werden. Anschließend wird die Anwendung ruft eine Verbindungsfunktion und übergibt sie den Namen der ausgewählten Datenquelle.  
  
 Wenn eine Datenquelle nicht angegeben ist, wird die Standarddatenquelle, angegeben durch die Systeminformationen verwendet. (Weitere Informationen finden Sie unter [Standard Unterschlüssel](../../../odbc/reference/install/default-subkey.md).) Wenn **SQLConnect** wird aufgerufen, mit einem *ServerName* Argument, das nicht gefunden werden kann, ist ein null-Zeiger oder ist "DEFAULT", der Treiber-Manager stellt eine Verbindung her mit der Standard-Datenquelle. Der Standardwert, der Datenquelle auch verwendet werden, wird Wenn die Verbindungszeichenfolge, die in einem Aufruf verwendet **SQLDriverConnect** oder **SQLBrowseConnect** enthält die **DSN** Schlüsselwortgruppe auf "Standard "oder wenn die angegebene Datenquelle nicht gefunden wird. Darüber hinaus wird der Standardwert, der Datenquelle verwendet wird, wenn die Verbindungszeichenfolge, die in einem Aufruf verwendet **SQLDriverConnect** enthält nicht die **DSN** Schlüsselwort.  
  
 Mit einem dateibasierten Treibern ist es möglich, ein Paradigma für die Datei zu verwenden. Für die Daten auf dem lokalen Computer gespeichert sind wissen Benutzer häufig, dass ihre Daten in einer bestimmten Datei, z. B. nützlich ist. Anstelle einer unbekannten Datenquelle zu verwenden, ist es einfacher für solche Benutzer aus, um die Datei auszuwählen, die sie kennen. Zur Implementierung, ruft die Anwendung zuerst **SQLDrivers**. Diese Funktion wird vom Treiber-Manager implementiert und kann aufgerufen werden, bevor alle Treiber geladen werden. **SQLDrivers** gibt eine Liste der verfügbaren Treiber; sie gibt überdies die Werte für die **FileUsage** und **FileExtns** Schlüsselwörter. Die **FileUsage** Schlüsselwort wird erläutert, gibt an, ob dateibasierten Treibern Dateien als Tabellen behandeln, als Xbase ist, oder als Datenbanken, wie der Fall ist Microsoft® Access. Die **FileExtns** Schlüsselwort Listet die Dateinamenerweiterungen der Treiber, wie z. B. DBF für eine Xbase-Treiber erkennt. Mithilfe dieser Informationen erstellt die Anwendung ein Dialogfeld, das über die der Benutzer eine Datei auswählt. Basierend auf der Erweiterung der ausgewählten Datei, klicken Sie dann die Anwendung stellt eine Verbindung her an den Treiber durch den Aufruf **SQLDriverConnect** mit der **Treiber** Schlüsselwort.  
  
 Es gibt nichts zu einer Anwendung mithilfe einer Datenquelle mit einem dateibasierten Treiber oder das Aufrufen **SQLDriverConnect** mit der **Treiber** Schlüsselwort, um die Verbindung mit einer DBMS-basierten Treibers. Hier sind einige häufige Verwendungen von der **Treiber** -Schlüsselwort für DBMS-basierten Treibern:  
  
-   **Erstellen keine Datenquellen.** Eine benutzerdefinierte Anwendung kann z. B. einen bestimmten Treiber und eine Datenbank verwenden. Wenn der Name des Treibers und alle Informationen, der erforderlich sind, für die Verbindung mit der Datenbank ist in der Anwendung hartcodiert, müssen Benutzer nicht auf ihrem Computer zum Ausführen der Anwendung eine Datenquelle zu erstellen. Alles, was sie tun müssen wird die Anwendung und die Treiber zu installieren.  
  
     Ein Nachteil dieser Methode ist, dass die Anwendung neu kompiliert und verteilt werden, wenn die Verbindungsinformationen geändert werden muss. Wenn der Name der Datenquelle in der Anwendung anstelle von vollständigen Verbindungsinformationen hartcodiert ist, muss jeder Benutzer nur die Informationen in der Datenquelle ändern.  
  
-   **Zugriff auf ein bestimmtes DBMS ein einziges Mal aus.** Beispielsweise kann eine Tabelle, die Daten abruft, durch Aufrufen von ODBC-Funktionen enthalten die **Treiber** Schlüsselwort, um einen bestimmten Treiber zu identifizieren. Da der Treibername für alle Benutzer von Bedeutung, die diesen Treiber verfügen ist, kann das Arbeitsblatt von diesen Benutzern übergeben werden. Wenn das Arbeitsblatt Name der Datenquelle enthalten, würde jeder Benutzer verfügen, zum Erstellen der gleichen Datenquelle, um das Arbeitsblatt zu verwenden.  
  
-   **Durchsuchen das System für alle Datenbanken auf einen bestimmten Treiber zugreifen kann.** Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)weiter unten in diesem Abschnitt.
