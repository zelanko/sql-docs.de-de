---
description: Visual C++-Erweiterungen für ADO
title: Visual C++ Erweiterungen für ADO | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6d1586800288d0a2d2984cf08e770f776c5ee3c6
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991811"
---
# <a name="visual-c-extensions-for-ado"></a>Visual C++-Erweiterungen für ADO
Die bevorzugte Methode zum Programmieren von ADO mit Visual C++ ist die Verwendung der **#Import** -Direktive, wie in [Microsoft Visual C++ ADO-Programmierung](./visual-c-ado-programming.md)erläutert. In früheren Versionen von ADO gab es jedoch eine Alternative Programmiermethode mithilfe von Visual C++: die Visual C++ Erweiterungen. In diesem Abschnitt wird dieses Feature für diejenigen beschrieben, die Visual C++-Erweiterungs Code verwalten müssen, aber mit #**Import**muss neuer ADO-Code geschrieben werden.

 Einer der aktivsten Aufträge Visual C++ Programmierern beim Abrufen von Daten mit ADO ist das Konvertieren von Daten, die als Variant-Datentyp zurückgegeben werden, in einen C++-Datentyp und das anschließende Speichern der konvertierten Daten in einer Klasse oder Struktur. Das Abrufen von C++-Daten über einen Variant-Datentyp ist nicht nur mühsam, sondern verringert auch die Leistung.

 ADO stellt eine Schnittstelle bereit, die das Abrufen von Daten in systemeigene C/C++-Datentypen unterstützt, ohne dass ein Variant durchlaufen wird. Außerdem werden Präprozessormakros bereitgestellt, die die Verwendung der Das Ergebnis ist ein flexibles Tool, das einfacher zu verwenden ist und eine hohe Leistung aufweist.

 Ein häufiges c/C++-Client Szenario besteht darin, einen Datensatz in einem [Recordset](../../reference/ado-api/recordset-object-ado.md) an eine c/C++-Struktur oder-Klasse zu binden, die systemeigene c/C++-Typen enthält. Beim Durchlaufen von Varianten müssen Sie den Konvertierungs Code von Variant in Native C/C++-Typen schreiben. Die Visual C++ Erweiterungen für ADO sind darauf ausgerichtet, dieses Szenario für die Visual C++ Programmierern viel einfacher zu gestalten.

 Weitere Informationen zu den Visual C++-Erweiterungen für ADO finden Sie in den folgenden Themen.

-   [Verwenden von Visual C++-Erweiterungen für ADO](./using-visual-c-extensions.md)

-   [Visual C++-Erweiterungsheader](./visual-c-extensions-header.md)

-   [Beispiel für ADO mit Visual C++ Erweiterungen](./visual-c-extensions-example.md)

## <a name="see-also"></a>Weitere Informationen
 [ADO for Visual C++ Syntax Index for com](../../reference/ado-api/ado-for-visual-c-syntax-index-for-com.md) [Visual C++ Extensions example](./visual-c-extensions-example.md) [using Visual C++ Extensions](./using-visual-c-extensions.md) [Visual C++ Extensions Header](./visual-c-extensions-header.md)