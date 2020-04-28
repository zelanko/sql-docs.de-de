---
title: Eindeutigen Befehl festlegen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7d3d37509450d1305891100b37bfd1ad026166e8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300840"
---
# <a name="set-unique-command"></a>SET UNIQUE-Befehl
Gibt an, ob Datensätze mit doppelten Index Schlüsselwerten in einer Indexdatei verwaltet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 EIN  
 Gibt an, dass alle Datensätze mit einem doppelten Index Schlüsselwert nicht in der Indexdatei enthalten sein sollen. Nur der erste Datensatz mit dem ursprünglichen Index Schlüsselwert ist in der Indexdatei enthalten.  
  
 OFF  
 (Standard) Gibt an, dass Datensätze mit doppelten Index Schlüsselwerten in der Indexdatei enthalten sein sollen.  
  
## <a name="remarks"></a>Bemerkungen  
 Bei der Ausgabe von REINDEX wird eine Indexdatei beibehalten. Weitere Informationen finden Sie unter [Index](../../odbc/microsoft/index-command.md).
