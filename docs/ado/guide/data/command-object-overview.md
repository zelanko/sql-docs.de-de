---
title: Übersicht über das Befehls | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- command object [ADO]
ms.assetid: e84a14b1-3c2a-4f7d-a966-9e08a93948df
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 808c63575b93f9e4fa3b6459d2111637021218c1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472719"
---
# <a name="command-object-overview"></a>Command-Objekt – Übersicht
Mit einem **Befehl** -Objekts können Sie folgende Möglichkeiten:  
  
-   Definieren Sie die ausführbare Datei Text des Befehls (z. B. eine SQL-Anweisung oder eine gespeicherte Prozedur) mithilfe der **CommandText** Eigenschaft.  
  
-   Parametrisierte Abfragen oder gespeicherte Prozedurargumente definieren, indem **Parameter** Objekte und die **Parameter** Auflistung.  
  
-   Ausführen ein Befehls und zum Zurückgeben einer **Recordset** Objekt, falls zutreffend, mithilfe der **Execute** Methode.  
  
-   Geben Sie den Befehl unter Verwendung der **CommandType** Eigenschaft vor der Ausführung, um die Leistung optimieren.  
  
-   Geben Sie bestimmte Informationen zu den Befehlstext mithilfe der **Dialekt** Eigenschaft der **Befehl** Objekt.  
  
-   Steuern, ob der Anbieter eine vorbereitete (oder kompilierte) Version des Befehls vor der Ausführung mit speichert die **Prepared** Eigenschaft.  
  
-   Legen Sie die Anzahl der Sekunden, die ein Anbieter, bis ein Befehl zum Ausführen wartet, indem Sie mit der **"CommandTimeout"** Eigenschaft.  
  
-   Ordnen Sie eine offene Verbindung mit einem **Befehl** Objekt durch Festlegen seiner **ActiveConnection** Eigenschaft.  
  
-   Legen Sie die **Namen** Eigenschaft zum Identifizieren der **Befehl** Objekt als Methode für das zugeordnete **Verbindung** Objekt.  
  
-   Übergeben einer **Befehl** -Objekt die **Quelle** Eigenschaft eine **Recordset** um Daten zu erhalten.  
  
-   Übergeben Sie einen **Stream** Objekt, das an einen Anbieter, die er unterstützt einen Befehl (z. B. eine XML-Befehl) enthält.
