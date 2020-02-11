---
title: Einschränkungen der CREATE TABLE-Anweisung | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: db5d2cb8decde9828acd3005551717ac9f6cef32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096592"
---
# <a name="create-table-statement-limitations"></a>Einschränkungen der CREATE TABLE-Anweisung
Wenn Microsoft Access, Microsoft Excel oder paradoxidriver verwendet wird und die Länge einer Text-oder Binary-Spalte nicht angegeben wird (oder als 0 angegeben wird), wird die Spaltenlänge auf 255 festgelegt.  
  
 Wenn der dBase-Treiber verwendet wird und die Länge einer Text-oder Binary-Spalte nicht angegeben wird (oder als 0 angegeben wird), wird die Spaltenlänge auf 254 festgelegt.  
  
 Maximal 255 Spalten werden unterstützt.  
  
 Wenn der Microsoft Excel-Treiber in einer Datenquelle vom Typ "mikrosoftexcel 5,0, 7,0 oder 97" verwendet wird, kann kein Arbeitsblatt mit dem gleichen Namen wie ein zuvor gelöschter Arbeitsblatt erstellt werden. Wenn der Microsoft Excel-Treiber verwendet wird, um auf ein Arbeitsblatt der Version 5,0, 7,0 oder 97 zuzugreifen, löscht eine DROP TABLE-Anweisung das Arbeitsblatt, löscht jedoch nicht den Namen des Arbeitsblatts.  
  
 Wenn der Paradox-Treiber verwendet wird, können Spalten nicht hinzugefügt werden, nachdem ein Index für eine Tabelle definiert wurde. Wenn die erste Spalte der Argumentliste einer CREATE TABLE-Anweisung einen Index erstellt, kann keine zweite Spalte in der Argumentliste enthalten sein.
