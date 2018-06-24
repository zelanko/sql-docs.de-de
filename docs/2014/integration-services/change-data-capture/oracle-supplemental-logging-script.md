---
title: Ergänzendes Oracle-Protokollierungsskript | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5e6ee618-b89b-46c7-92ad-4fc5ef7b777a
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 04e2c152da025473f049159a8e9eff4f4d28c3c2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050841"
---
# <a name="oracle-supplemental-logging-script"></a>Ergänzendes Oracle-Protokollierungsskript
  In diesem Dialogfeld wird das ergänzende Oracle-Protokollierungsskript angezeigt.  
  
 Wenn Sie eine CDC-Instanz für die Verwendung vorbereiten, erstellt der CDC Designer ein Oracle SQL-Skript, mit dem die ergänzende Protokollierung für die aufzuzeichnenden Tabellen eingerichtet wird. Das ergänzende Protokollierungsskript weist Oracle an, dass beim Aktualisieren einer bestimmten Tabelle die Änderungsdatensätze, die in das Transaktionsprotokoll geschrieben werden, die Daten aller wichtigen Spalten enthalten sollen, nicht nur die Spalten, die sich geändert haben.  
  
 Je nach den Oracle DBA-Richtlinien in Ihrer Organisation kann es erforderlich sein, dass beim Ausführen des ergänzenden Protokollierungsskripts eine Überprüfung und Genehmigung durch einen Oracle-Datenbankadministrator erfolgt.  
  
## <a name="options"></a>Tastatur  
 Sie können die folgenden Optionen verwenden, um festzulegen, wie das Skript ausgeführt wird.  
  
 **Run Script**  
 Führt das ergänzende Protokollierungsskript für die Tabellen aus, die für die CDC-Instanz definiert wurden. Zum Ausführen dieses Skripts muss der Oracle-Benutzer über die ALTER TABLE-Berechtigung für alle zu erfassenden Tabellen und die SELECT-Berechtigung für die DBA_LOG_GROUPS-Sicht verfügen. Außerdem muss der Oracle-Benutzer die Anmeldeinformationen für eine Oracle-Datenbankverwendung mit den erforderlichen Berechtigungen besitzen. Sie können auf die Aufforderung des Programms zur Eingabe der Oracle-Anmeldeinformationen warten, und dann die Ausführung des Skripts folgen lassen.  
  
 **Speichern unter**  
 Speichert das Skript als Textdatei. Diese Option wird verwendet, wenn ein Oracle-Datenbankadministrator das ergänzende Protokollierungsskript untersuchen und ausführen muss und wenn das Programm das Speichern des Skripts in einer Textdatei zulässt, die Sie später per E-Mail an den Oracle-Datenbankadministrator senden oder auf andere Art für die spätere Ausführung bereitstellen können (mithilfe des SQL*Plus Oracle-Hilfsprogramms oder eines anderen Tools zum Ausführen von Skripts für eine Oracle-Datenbank).  
  
 **Kopieren**  
 Kopiert das Skript in die Zwischenablage. Nach Abschluss des Vorgangs können Sie das Skript an jedem erforderlichen Speicherort einfügen, falls ein Oracle-Datenbankadministrator das ergänzende Protokollierungsskript untersuchen und ausführen muss.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Verwalten einer CDC-Instanz](manage-a-cdc-instance.md)   
 [Verwalten einer CDC-Instanz](manage-a-cdc-instance.md)  
  
  