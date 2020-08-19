---
description: Binden von Spalten für die Verwendung mit Blockcursorn
title: Binden von Spalten für die Verwendung mit Block Cursorn | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column-wise binding [ODBC]
- row-wise binding [ODBC]
- result sets [ODBC], binding columns
- cursors [ODBC], block
- binding columns [ODBC]
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 231beede-cdfa-4e28-8b10-2760b983250f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a58e6359bd7b0ad5d44f75a3d844ef2e9872f2a8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429442"
---
# <a name="binding-columns-for-use-with-block-cursors"></a>Binden von Spalten für die Verwendung mit Blockcursorn
Da Block Cursor mehrere Zeilen zurückgeben, müssen Anwendungen, die Sie verwenden, anstelle einer einzelnen Variablen ein Array von Variablen an jede Spalte binden. Diese Arrays werden zusammen als *rowsetpuffer*bezeichnet. Im folgenden sind die beiden Bindungsarten aufgeführt:  
  
-   Binden Sie ein Array an jede Spalte. Dies wird *spaltenweise Bindung* genannt, da jede Datenstruktur (Array) Daten für eine einzelne Spalte enthält.  
  
-   Definieren Sie eine Struktur, in der die Daten für eine ganze Zeile enthalten sind, und binden Sie ein Array dieser Strukturen. Dies wird *zeilenweise Bindung* genannt, da jede Datenstruktur die Daten für eine einzelne Zeile enthält.  
  
 Wenn die Anwendung einzelne Variablen an Spalten bindet, ruft Sie **SQLBindCol** auf, um Arrays an Spalten zu binden. Der einzige Unterschied besteht darin, dass es sich bei den bestandenen Adressen um Array Adressen handelt, nicht um einzelne Variablen Die Anwendung legt das SQL_BIND_BY_COLUMN-Anweisungs Attribut fest, um anzugeben, ob die spaltenweise oder zeilenweise Bindung verwendet wird. Ob spaltenweise oder zeilenweise Bindung verwendet werden soll, ist größtenteils eine Frage der Anwendungs Einstellung. Die zeilenweise Bindung kann dem Layout von Daten der Anwendung genauer entsprechen. in diesem Fall würde Sie eine bessere Leistung bieten.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Spalten weises binden](../../../odbc/reference/develop-app/column-wise-binding.md)  
  
-   [Zeilenbezogenes Binden](../../../odbc/reference/develop-app/row-wise-binding.md)
