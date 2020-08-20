---
description: Scrollbare Cursor und Transaktionsisolation
title: Scrollbare Cursor und Transaktions Isolation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- isolation levels [ODBC]
- scrollable cursors [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: f0216f4a-46e3-48ae-be0a-e2625e8403a6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 790b2d0c4d80c821645c3a4360d1295cc55a8a4e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476502"
---
# <a name="scrollable-cursors-and-transaction-isolation"></a>Scrollbare Cursor und Transaktionsisolation
In der folgenden Tabelle sind die Faktoren aufgeführt, die die Sichtbarkeit von Änderungen bestimmen.  
  
|Vorgenommene Änderungen:|Sichtbarkeit ist abhängig von:|  
|----------------------|----------------------------|  
|Cursor|Cursortyp, Cursor Implementierung|  
|Andere Anweisungen in derselben Transaktion|Cursortyp|  
|Anweisungen in anderen Transaktionen|Cursortyp, Transaktions Isolationsstufe|  
  
 Diese Faktoren werden in der folgenden Abbildung dargestellt.  
  
 ![Faktoren, die die Sichtbarkeit der Änderungen steuern](../../../odbc/reference/develop-app/media/pr23.gif "pr23")  
  
 In der folgenden Tabelle werden die Möglichkeiten der einzelnen Cursor Typen zusammengefasst, um Änderungen zu erkennen, die von sich selbst, durch andere Vorgänge in der eigenen Transaktion und durch andere Transaktionen vorgenommen wurden. Die Sichtbarkeit der letzteren Änderungen hängt vom Cursortyp und der Isolationsstufe der Transaktion ab, die den Cursor enthält.  
  
|Cursor type\action|Self|Heimat<br /><br /> Transaktion|Andere<br /><br /> Transaktion<br /><br /> (Ru [a])|Andere<br /><br /> Transaktion<br /><br /> (RC [a])|Andere<br /><br /> Transaktion<br /><br /> (RR [a])|Andere<br /><br /> Transaktion<br /><br /> (S [a])|  
|-------------------------|----------|-----------------|----------------------------------|----------------------------------|----------------------------------|---------------------------------|  
|statischen|||||||  
|Einfügen|Vielleicht [b]|Nein|Nein|Nein|Nein|Nein|  
|Aktualisieren|Vielleicht [b]|Nein|Nein|Nein|Nein|Nein|  
|Löschen|Vielleicht [b]|Nein|Nein|Nein|Nein|Nein|  
|Keysetgesteuert|||||||  
|Einfügen|Vielleicht [b]|Nein|Nein|Nein|Nein|Nein|  
|Aktualisieren|Ja|Ja|Ja|Ja|Nein|Nein|  
|Löschen|Vielleicht [b]|Ja|Ja|Ja|Nein|Nein|  
|Dynamisch|||||||  
|Einfügen|Ja|Ja|Ja|Ja|Ja|Nein|  
|Aktualisieren|Ja|Ja|Ja|Ja|Nein|Nein|  
|Löschen|Ja|Ja|Ja|Ja|Nein|Nein|  
  
 [a] die Buchstaben in Klammern geben die Isolationsstufe der Transaktion an, die den Cursor enthält. die Isolationsstufe der anderen Transaktion (in der die Änderung vorgenommen wurde) ist irrelevant.  
  
 RU: Lesen ohne Commit  
  
 RC: Lesen mit Commit  
  
 RR: wiederholbarer Lesevorgang  
  
 S: serialisierbar  
  
 [b] hängt davon ab, wie der Cursor implementiert wird. Ob der Cursor solche Änderungen erkennen kann, wird über die SQL_STATIC_SENSITIVITY-Option in **SQLGetInfo**gemeldet.
