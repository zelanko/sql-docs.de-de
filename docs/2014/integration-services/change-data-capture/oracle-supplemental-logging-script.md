---
title: Ergänzendes Oracle-Protokollierungsskript | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5e6ee618-b89b-46c7-92ad-4fc5ef7b777a
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 41925225638ca278fb2d58ec1fddf1b8c9918ab5
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84922636"
---
# <a name="oracle-supplemental-logging-script"></a>Ergänzendes Oracle-Protokollierungsskript
  In diesem Dialogfeld wird das ergänzende Oracle-Protokollierungsskript angezeigt.  
  
 Wenn Sie eine CDC-Instanz für die Verwendung vorbereiten, erstellt der CDC Designer ein Oracle SQL-Skript, mit dem die ergänzende Protokollierung für die aufzuzeichnenden Tabellen eingerichtet wird. Das ergänzende Protokollierungsskript weist Oracle an, dass beim Aktualisieren einer bestimmten Tabelle die Änderungsdatensätze, die in das Transaktionsprotokoll geschrieben werden, die Daten aller wichtigen Spalten enthalten sollen, nicht nur die Spalten, die sich geändert haben.  
  
 Je nach den Oracle DBA-Richtlinien in Ihrer Organisation kann es erforderlich sein, dass beim Ausführen des ergänzenden Protokollierungsskripts eine Überprüfung und Genehmigung durch einen Oracle-Datenbankadministrator erfolgt.  
  
## <a name="options"></a>Tastatur  
 Sie können die folgenden Optionen verwenden, um festzulegen, wie das Skript ausgeführt wird.  
  
 **Skript ausführen**  
 Führt das ergänzende Protokollierungsskript für die Tabellen aus, die für die CDC-Instanz definiert wurden. Zum Ausführen dieses Skripts muss der Oracle-Benutzer über die ALTER TABLE-Berechtigung für alle zu erfassenden Tabellen und die SELECT-Berechtigung für die DBA_LOG_GROUPS-Sicht verfügen. Außerdem muss der Oracle-Benutzer die Anmeldeinformationen für eine Oracle-Datenbankverwendung mit den erforderlichen Berechtigungen besitzen. Sie können auf die Aufforderung des Programms zur Eingabe der Oracle-Anmeldeinformationen warten, und dann die Ausführung des Skripts folgen lassen.  
  
 **Speichern unter**  
 Speichert das Skript als Textdatei. Diese Option wird verwendet, wenn ein Oracle-Datenbankadministrator das ergänzende Protokollierungsskript untersuchen und ausführen muss und wenn das Programm das Speichern des Skripts in einer Textdatei zulässt, die Sie später per E-Mail an den Oracle-Datenbankadministrator senden oder auf andere Art für die spätere Ausführung bereitstellen können (mithilfe des SQL*Plus Oracle-Hilfsprogramms oder eines anderen Tools zum Ausführen von Skripts für eine Oracle-Datenbank).  
  
 **Copy**  
 Kopiert das Skript in die Zwischenablage. Nach Abschluss des Vorgangs können Sie das Skript an jedem erforderlichen Speicherort einfügen, falls ein Oracle-Datenbankadministrator das ergänzende Protokollierungsskript untersuchen und ausführen muss.  
  
## <a name="see-also"></a>Weitere Informationen  
 [How to Manage a CDC Instance](manage-a-cdc-instance.md)   
 [Verwalten einer CDC-Instanz](manage-a-cdc-instance.md)  
  
  
