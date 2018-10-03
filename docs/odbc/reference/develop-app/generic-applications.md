---
title: Allgemeiner Anwendungen | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 59110f66c512845ff5ce1f2f246c05c63fa755b9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751284"
---
# <a name="generic-applications"></a>Allgemeine Anwendungen
Allgemeine Anwendungen manchmal eine hartcodierte Aufgabe ausführen, z. B. als Kalkulationstabelle, die Abrufen von Daten aus einer Datenbank. Sie können auch eine Vielzahl von benutzerdefinierten Aufgaben, z. B. eine Standardabfrage-Anwendung, die der Benutzer zum eingeben und Ausführen einer SQL-Anweisung ausführen. Was allgemeine Anwendungen gemeinsam haben, ist, dass sie mit einer Vielzahl von verschiedenen DBMS-Systeme funktionieren müssen und der Entwickler nicht im Voraus weiß, welche diese DBMS werden.  
  
 Aus diesem Grund müssen allgemeine Anwendungen hochgradig interoperabel sein. Der Entwickler muss stellen viele Optionen, trading aus Interoperabilität für Funktionen, und muss Code schreiben, der erwartet, Treiber dass, um eine Vielzahl von Funktionen zu unterstützen. Während allgemeine Anwendungen optimiert werden können, um mit beliebten DBMS zu arbeiten, enthalten sie selten treiberspezifische oder DBMS-spezifischen Code.
