---
title: Einschränkungen beim UPDATE-Anweisung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a6b854cc417898c5576c60ca129c597eae280df4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62633132"
---
# <a name="update-statement-limitations"></a>Einschränkungen der UPDATE-Anweisung
Für die Paradox-Treiber, um eine Tabelle zu aktualisieren muss die Tabelle einen eindeutigen Index (Paradox-Primärschlüssel) verfügen. Wenn Sie die Paradox-Treiber verwenden, ohne die Datenbank-Engine für Borland implementieren zu müssen, ist es nicht möglich, eine Paradox-Tabelle zu aktualisieren.  
  
 Durch den Text-Treiber unterstützt nicht.  
  
 Wenn der Microsoft Excel-Treiber verwendet wird, es ist möglich, Werte zu aktualisieren, aber eine Zeile in eine Tabelle basierend auf Microsoft Excel-Arbeitsblatt nicht gelöscht werden kann. Die UPDATE-Anweisung wird daher nicht offiziell von Microsoft Excel-Treiber unterstützt angesehen. Nur INSERT-Anweisung wird als unterstützt betrachtet.
