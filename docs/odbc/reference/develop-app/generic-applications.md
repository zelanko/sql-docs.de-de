---
title: Generische Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], generic applications
- interoperability [ODBC], levels
- generic applications [ODBC]
ms.assetid: dda2a3c4-76ef-40a6-b3a1-9e95bed61618
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6b1544f5562468db03a649c263993039a722a3c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139300"
---
# <a name="generic-applications"></a>Allgemeine Anwendungen
Generische Anwendungen führen manchmal eine hart codierte Aufgabe aus, z. b. eine Kalkulations Tabelle, die Daten aus einer Datenbank abruft. Sie können auch eine Vielzahl von benutzerdefinierten Aufgaben ausführen, wie z. b. eine generische Abfrageanwendung, die es dem Benutzer ermöglicht, eine SQL-Anweisung einzugeben und auszuführen. Welche generischen Anwendungen gemeinsam verwendet werden, besteht darin, dass Sie mit einer Vielzahl von unterschiedlichen DBMSs arbeiten müssen und dass der Entwickler im Voraus nicht weiß, was diese DBMSs-Daten sind.  
  
 Daher müssen generische Anwendungen hochgradig interoperabel sein. Der Entwickler muss viele Möglichkeiten treffen, Interoperabilität für Features zu beenden und Code schreiben, der die Treiber für eine Vielzahl von Funktionen erwartet. Obwohl generische Anwendungen möglicherweise für gängige DBMSs optimiert werden, enthalten Sie nur selten treiberspezifischen oder DBMS-spezifischen Code.
