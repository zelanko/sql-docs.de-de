---
description: Abrufen von Daten
title: Daten werden erhalten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, getting data
ms.assetid: 3931e7ec-f66b-4d5d-aad3-c4bf12e8b154
author: rothja
ms.author: jroth
ms.openlocfilehash: 3223d2291ba15ab0a2c14b1fac2aaea911bde395
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980771"
---
# <a name="getting-data"></a>Abrufen von Daten
In den ADO.net- [Grundlagen](./ado-fundamentals.md)und im [HelloData](./hellodata-a-simple-ado-application.md) -Beispiel wurden die vier Haupt Vorgänge zum Erstellen einer ADO-Anwendung eingeführt: das Erstellen von Daten, das Untersuchen von Daten, das Bearbeiten von Daten und das Aktualisieren von Daten. In diesem Abschnitt wird erläutert, wie Sie Daten ausführlicher erhalten.  
  
 Auf einer grundlegenden Ebene tragen mehrere ADO-Objekte zu den Vorgängen zum erhalten von Daten bei. Zuerst müssen Sie mithilfe eines ADO- **Verbindungs** Objekts eine Verbindung mit einer Datenquelle herstellen. Anschließend übergeben Sie mithilfe eines ADO- **Befehls** Objekts Anweisungen an die Datenquelle. Schließlich erhalten Sie am häufigsten Daten in einem ADO- **Recordset** -Objekt.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Herstellen einer Verbindung mit Datenquellen](./connecting-to-data-sources.md)  
  
-   [Vorbereiten und Ausführen von Befehlen](./preparing-and-executing-commands.md)  
  
-   [Empfangen von Ergebnissen](./receiving-results.md)