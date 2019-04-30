---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df7a2d036692cefcd1b2ea2338d51938a11ea85a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208435"
---
# <a name="vertical-applications"></a>Vertikale Anwendungen
Vertikale Anwendungen führen in der Regel eine klar definierte Aufgabe für eine einzelne DBMS. Auftragserfassungsanwendung verfolgt z. B. die Bestellungen in einem Unternehmen. Was diese Arten von Anwendungen gemeinsam haben ist, dass das Datenbankschema in der Regel durch Anwendungsentwickler vorgesehen, während die Anwendung mit einer Reihe von verschiedenen DBMS arbeiten kann, es mit einer einzelnen DBMS für einen einzelnen Kunden funktioniert.  
  
 Da vertikale Anwendungen in der Regel auf bestimmte Funktionen, z. B. scrollfähige Cursor oder Transaktionen, erfordern unterstützen sie nur selten allen DBMS. Stattdessen sind sie tendenziell hochgradig interoperabel auf eine begrenzte Anzahl von DBMS-Systeme. Wählen Sie in der Regel vertikal Anwendungsentwickler, die DBMS-Systeme zu unterstützen, die einen Großteil des Markts darstellen, und ignorieren den Rest. Sie können sogar entscheiden, um bestimmte Treiber für diese DBMS, um ihre Tests zu reduzieren und die Supportkosten Produkt zu unterstützen.  
  
 Da vertikale Anwendungen auf einen bekannten Satz von DBMS-Systeme unterstützen können, enthalten diese treiberspezifische oder DBMS-spezifischen Code. Solcher Code ist jedoch am besten auf ein Minimum reduziert, da sie zusätzliche Zeit für die Verwaltung erfordert.
