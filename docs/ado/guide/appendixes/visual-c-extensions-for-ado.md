---
title: Visual C++-Erweiterungen für ADO | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO], VC++ extensions for ADO
ms.assetid: 2952ece0-7217-4448-bb09-f6b64f43b7e2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4432c125b0c860775911aa753984806a472a64ba
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864497"
---
# <a name="visual-c-extensions-for-ado"></a>Visual C++-Erweiterungen für ADO
Die bevorzugte Methode für das Programmieren von ADO mit Visual C++ verwendet den **#import** Richtlinie, wie unter [Microsoft Visual C++-ADO-Programmierung](../../../ado/guide/appendixes/visual-c-ado-programming.md). Frühere Versionen von ADO jedoch geliefert, mit einer alternativen Methode der Programmierung mit Visual C++: Visual C++-Erweiterungen. Dieser Abschnitt beschreibt diese Funktion für diejenigen, die Erweiterungen der Visual C++-Code verwalten müssen, aber neuer ADO-Code mit # geschrieben werden soll**importieren**.

 Eine der aufwändigsten Aufträge Visual C++-Programmierer Schriftart beim Abrufen von Daten mit ADO als VARIANT-Datentyp in einen C++-Datentyp zurückgegeben, und Speichern der konvertierten Daten in einer Klasse oder Struktur konvertieren von Daten ist. Abrufen von C++-Daten über einen VARIANT-Datentyp umständlich, sondern beeinträchtigt Leistung ist.

 ADO stellt eine Schnittstelle, die beim Abrufen von Daten in systemeigenen C/C++-Datentypen unterstützt werden, ohne Umweg über eine Variante bereit und bietet außerdem Präprozessormakros, die mithilfe der Benutzeroberfläche zu vereinfachen. Das Ergebnis ist ein flexibles Tool, das ist einfacher zu verwenden und bietet hervorragende Leistung.

 Ein häufiges Szenario der C/C++-Client ist, binden Sie einen Datensatz in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) auf eine C/C++-Struktur oder Klasse, die mit systemeigenen C/C++-Typen. Bei der Verwendung von VARIANTs umfasst das Schreiben von Code für die Konvertierung von Varianten in systemeigenen C/C++-Typen. Visual C++-Erweiterungen für ADO gelten zu diesem Szenario für den Visual C++-Programmierer viel einfacher gestalten.

 Finden Sie unter den folgenden Themen Weitere Informationen zu den Visual C++-Erweiterungen für ADO.

-   [Mithilfe von Visual C++-Erweiterungen für ADO](../../../ado/guide/appendixes/using-visual-c-extensions.md)

-   [Visual C++-Erweiterungsheader](../../../ado/guide/appendixes/visual-c-extensions-header.md)

-   [ADO mit Visual C++-Erweiterungen – Beispiel](../../../ado/guide/appendixes/visual-c-extensions-example.md)

## <a name="see-also"></a>Siehe auch
 [ADO für Visual C++ – Syntaxindex für COM-](../../../ado/reference/ado-api/ado-for-visual-c-syntax-index-for-com.md) [Visual C++-Erweiterungen – Beispiel](../../../ado/guide/appendixes/visual-c-extensions-example.md) [mithilfe von Visual C++-Erweiterungen](../../../ado/guide/appendixes/using-visual-c-extensions.md) [Visual C++-Erweiterungsheader](../../../ado/guide/appendixes/visual-c-extensions-header.md)
