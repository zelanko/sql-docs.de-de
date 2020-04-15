---
title: Vertikale Anwendungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], vertical applications
- vertical applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: d50ea3e6-7a9e-4fb6-8cd8-1d429d2f7b3c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc88f38fd1ffe8b2ee0033ad0a2abc4f15fd5cf3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300375"
---
# <a name="vertical-applications"></a>Vertikale Anwendungen
Vertikale Anwendungen führen in der Regel eine klar definierte Aufgabe für ein einzelnes DBMS aus. Beispielsweise verfolgt eine Auftragserfassungsanwendung die Aufträge in einem Unternehmen. Diese Anwendungstypen haben gemeinsam, dass das Datenbankschema in der Regel vom Anwendungsentwickler entworfen wird und die Anwendung zwar mit verschiedenen DBMS arbeitet, aber mit einem einzelnen DBMS für einen einzelnen Kunden arbeitet.  
  
 Da vertikale Anwendungen in der Regel bestimmte Funktionen erfordern, z. B. scrollbare Cursor oder Transaktionen, unterstützen sie selten alle DBMS. Stattdessen sind sie in der Regel in einer begrenzten Gruppe von DBMS sehr interoperabel. In der Regel entscheiden sich vertikale Anwendungsentwickler dafür, diese DBMS zu unterstützen, die einen großen Teil des Marktes ausmachen, und den Rest zu ignorieren. Sie können sogar bestimmte Treiber für diese DBMS unterstützen, um ihre Test- und Produktsupportkosten zu senken.  
  
 Da vertikale Anwendungen einen bekannten Satz von DBMS unterstützen können, enthalten sie manchmal treiber- oder DBMS-spezifischen Code. Dieser Code wird jedoch am besten auf ein Minimum beschränkt, da die Wartung zusätzliche Zeit erfordert.
