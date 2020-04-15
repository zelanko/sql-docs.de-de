---
title: CREATE TABLE-Anweisungsbeschränkungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE TABLE statement limitations [ODBC]
- ODBC SQL grammar, CREATE TABLE statement limitations
ms.assetid: c5067855-20c9-456f-8d63-f375b4297f2e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a83acb061cf8192dff1c6adede349f49a0b0bbdb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280871"
---
# <a name="create-table-statement-limitations"></a>Einschränkungen der CREATE TABLE-Anweisung
Wenn Microsoft Access, Microsoft Excel oder Paradoxdriver verwendet wird und die Länge einer Text- oder Binärspalte nicht angegeben ist (oder als 0 angegeben ist), wird die Spaltenlänge auf 255 festgelegt.  
  
 Wenn der dBASE-Treiber verwendet wird und die Länge einer Text- oder Binärspalte nicht angegeben ist (oder als 0 angegeben ist), wird die Spaltenlänge auf 254 festgelegt.  
  
 Es werden maximal 255 Spalten unterstützt.  
  
 Wenn der Microsoft Excel-Treiber in einer MicrosoftExcel 5.0-, 7.0- oder 97-Datenquelle verwendet wird, kann ein Arbeitsblatt nicht mit demselben Namen wie ein zuvor gelöschtes Arbeitsblatt erstellt werden. Wenn der Microsoft Excel-Treiber für den Zugriff auf ein Arbeitsblatt der Version 5.0, 7.0 oder 97 verwendet wird, löscht eine DROP TABLE-Anweisung das Arbeitsblatt, löscht jedoch nicht den Arbeitsblattnamen.  
  
 Wenn der Paradox-Treiber verwendet wird, können Keine Spalten hinzugefügt werden, nachdem ein Index für eine Tabelle definiert wurde. Wenn die erste Spalte der Argumentliste einer CREATE TABLE-Anweisung einen Index erstellt, kann eine zweite Spalte nicht in die Argumentliste aufgenommen werden.
