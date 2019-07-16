---
title: Anzahl der Datensätze | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- record count [ODBC]
- descriptors [ODBC], record count
ms.assetid: 46eec3cc-0ecc-4980-9020-fb74a9af5730
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d4d684fb6d9614defdca3897c53c4bae9fc231a9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138081"
---
# <a name="record-count"></a>Anzahl der Datensätze
Das Headerfeld SQL_DESC_COUNT ein Deskriptor ist die 1-basierte Index des höchsten Datensatzes, der Daten enthält. Dieses Feld ist nicht die Anzahl der allen Spalten oder Parametern, die gebunden sind. Wenn ein Deskriptor zugeordnet ist, ist der Anfangswert des SQL_DESC_COUNT 0.  
  
 Der Treiber hat eine Aktion zum Zuweisen und verwalten alle gewünschten Speicher zum Speichern von Informationen der Sicherheitsbeschreibung benötigt. Die Anwendung nicht explizit angeben der Größe eines Deskriptors noch reservieren neue Datensätze. Wenn die Anwendung zu einem anwendungsparameterdeskriptor-Datensatz bereitstellt, deren Anzahl größer als der Wert des SQL_DESC_COUNT ist, wird der Treiber automatisch SQL_DESC_COUNT erhöht. Wenn die Anwendung hebt die Bindung der höchsten anwendungsparameterdeskriptor-Datensatz, sinkt der Treiber automatisch SQL_DESC_COUNT, um die Anzahl von den höchsten verbleibenden gebundenen Datensatz enthalten.
