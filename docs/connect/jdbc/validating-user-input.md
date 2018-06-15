---
title: Validieren von Benutzereingaben | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8aa867b0-e6f0-49eb-93d3-817ae2ed8f77
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 438f65ae8ec719339297b62e9bef7c347a063a1b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32851225"
---
# <a name="validating-user-input"></a>Überprüfen der Benutzereingabe
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Wenn Sie eine Anwendung erstellen, die auf Daten zugreift, sollten Sie davon ausgehen, dass alle Benutzereingaben böswillig sind, solange nicht das Gegenteil bewiesen ist. Andernfalls ist die Anwendung anfällig für Angriffe. Eine Art von Angriff, die auftreten können wird als SQL Injection bezeichnet, dabei wird böswilliger Code an Zeichenfolgen angefügt, die später mit einer Instanz von übergeben werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] analysiert und ausgeführt werden kann. Zum Verhindern solcher Angriffe sollten Sie, wenn möglich, gespeicherte Prozeduren mit Parametern verwenden und Benutzereingaben immer überprüfen.  
  
 Das Überprüfen von Benutzereingaben im Clientcode ist wichtig, damit Sie keine Roundtrips zum Server verschwenden. Es ist von genauso großer Wichtigkeit, Parameter für gespeicherte Prozeduren auf dem Server zu überprüfen, um Eingaben abzufangen, die ungültig sind und die clientseitige Überprüfung umgehen.  
  
 Weitere Informationen zu SQL Injection und Möglichkeiten, dies zu verhindern, finden Sie unter "SQL Injection" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Books Online. Weitere Informationen zum Überprüfen der Parameter der gespeicherten Prozedur finden Sie unter "gespeicherte Prozeduren ([!INCLUDE[ssDE](../../includes/ssde_md.md)])" und den untergeordneten Themen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Books Online.  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von JDBC-Treiberanwendungen](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
