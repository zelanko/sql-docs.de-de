---
description: Vertikale Anwendungen
title: Vertikale Anwendungen | Microsoft-Dokumentation
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
ms.openlocfilehash: a12be9247af3f273526dd08ee99ff7cc301af822
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421404"
---
# <a name="vertical-applications"></a>Vertikale Anwendungen
Vertikale Anwendungen führen in der Regel eine klar definierte Aufgabe für ein einzelnes DBMS aus. Beispielsweise werden die Bestellungen in einem Unternehmen nachverfolgt. Diese Arten von Anwendungen haben häufig den Wert, dass das Datenbankschema normalerweise vom Anwendungsentwickler entworfen wird und die Anwendung zwar mit einer Reihe von unterschiedlichen DBMSs funktioniert, aber mit einem einzelnen DBMS für einen einzelnen Kunden funktioniert.  
  
 Da vertikale Anwendungen normalerweise bestimmte Funktionen erfordern, z. b. scrollfähige Cursor oder Transaktionen, unterstützen Sie selten alle DBMSs. Stattdessen sind Sie in der Regel unter einem begrenzten Satz von DBMSs hochgradig interoperabel. In der Regel wählen vertikale Anwendungsentwickler diese DBMSs unterstützen, die einen großen Anteil des Markts darstellen und den Rest ignorieren. Sie können sogar bestimmte Treiber für diese DBMSs unterstützen, um die Test-und Produktsupport Kosten zu reduzieren.  
  
 Da vertikale Anwendungen einen bekannten Satz von DBMSs unterstützen können, enthalten Sie manchmal treiberspezifischen oder DBMS-spezifischen Code. Dieser Code wird jedoch am besten auf ein Minimum beschränkt, da für die Wartung zusätzliche Zeit erforderlich ist.
