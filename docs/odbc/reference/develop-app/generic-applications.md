---
title: Generische Anwendungen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 607676d5370f02ee1d39196bff9261bc897521ee
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305551"
---
# <a name="generic-applications"></a>Allgemeine Anwendungen
Generische Anwendungen führen manchmal eine hartcodierte Aufgabe aus, z. B. eine Kalkulationstabelle, die Daten aus einer Datenbank abruft. Sie können auch eine Vielzahl von benutzerdefinierten Aufgaben ausführen, z. B. eine generische Abfrageanwendung, mit der der Benutzer eine SQL-Anweisung eingeben und ausführen kann. Generische Anwendungen haben gemeinsam, dass sie mit einer Vielzahl von verschiedenen DBMS arbeiten müssen und dass der Entwickler nicht vorher weiß, was diese DBMS sein werden.  
  
 Daher müssen generische Anwendungen stark interoperabel sein. Der Entwickler muss viele Entscheidungen treffen, die Interoperabilität für Features abhandeln und Code schreiben, der erwartet, dass Treiber eine breite Palette von Funktionen unterstützen. Generische Anwendungen können zwar auf die Arbeit mit gängigen DBMS abgestimmt sein, enthalten jedoch selten treiber- oder DBMS-spezifischen Code.
