---
title: Scrollbare Cursor und Transaktionsisolation | Microsoft Docs
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
ms.openlocfilehash: 7e40278bd209132736aee2788b5648ffa84a44e6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304221"
---
# <a name="scrollable-cursors-and-transaction-isolation"></a>Scrollbare Cursor und Transaktionsisolation
In der folgenden Tabelle sind die Faktoren aufgeführt, die die Sichtbarkeit von Änderungen bestimmen.  
  
|Änderungen vorgenommen von:|Die Sichtbarkeit hängt von folgenden Faktoren ab:|  
|----------------------|----------------------------|  
|Cursor|Cursortyp, Cursorimplementierung|  
|Andere Aussagen in derselben Transaktion|Cursortyp|  
|Auszüge in anderen Transaktionen|Cursortyp, Transaktionsisolationsstufe|  
  
 Diese Faktoren werden in der folgenden Abbildung dargestellt.  
  
 ![Faktoren, die die Sichtbarkeit der Änderungen steuern](../../../odbc/reference/develop-app/media/pr23.gif "pr23")  
  
 In der folgenden Tabelle wird die Fähigkeit jedes Cursortyps zusammengefasst, Änderungen zu erkennen, die von sich selbst, von anderen Vorgängen in seiner eigenen Transaktion und von anderen Transaktionen vorgenommen wurden. Die Sichtbarkeit der letztgenannten Änderungen hängt vom Cursortyp und der Isolationsstufe der Transaktion ab, die den Cursor enthält.  
  
|Cursortyp-Aktion|Self|Eigenen<br /><br /> Txn|Othr<br /><br /> Txn<br /><br /> (RU[a])|Othr<br /><br /> Txn<br /><br /> (RC[a])|Othr<br /><br /> Txn<br /><br /> (RR[a])|Othr<br /><br /> Txn<br /><br /> (S[a])|  
|-------------------------|----------|-----------------|----------------------------------|----------------------------------|----------------------------------|---------------------------------|  
|statischen|||||||  
|Einfügen|Vielleicht[b]|Nein|Nein|Nein|Nein|Nein|  
|Aktualisieren|Vielleicht[b]|Nein|Nein|Nein|Nein|Nein|  
|Löschen|Vielleicht[b]|Nein|Nein|Nein|Nein|Nein|  
|Keyset-gesteuert|||||||  
|Einfügen|Vielleicht[b]|Nein|Nein|Nein|Nein|Nein|  
|Aktualisieren|Ja|Ja|Ja|Ja|Nein|Nein|  
|Löschen|Vielleicht[b]|Ja|Ja|Ja|Nein|Nein|  
|Dynamisch|||||||  
|Einfügen|Ja|Ja|Ja|Ja|Ja|Nein|  
|Aktualisieren|Ja|Ja|Ja|Ja|Nein|Nein|  
|Löschen|Ja|Ja|Ja|Ja|Nein|Nein|  
  
 [a] Die Buchstaben in Klammern geben die Isolationsstufe der Transaktion an, die den Cursor enthält; die Isolationsstufe der anderen Transaktion (in der die Änderung vorgenommen wurde) ist irrelevant.  
  
 RU: Ungebunden lesen  
  
 RC: Lesen engagiert  
  
 RR: Wiederholbares Lesen  
  
 S: Serialisierbar  
  
 [b] Abhängig davon, wie der Cursor implementiert wird. Ob der Cursor solche Änderungen erkennen kann, wird über die SQL_STATIC_SENSITIVITY-Option in **SQLGetInfo**gemeldet.
