---
title: Überprüfen von Benutzereingaben | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8aa867b0-e6f0-49eb-93d3-817ae2ed8f77
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8138b5fa17bb3cae6c1bdf079d3c562346156fd8
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923925"
---
# <a name="validating-user-input"></a>Überprüfen der Benutzereingabe

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Wenn Sie eine Anwendung erstellen, die auf Daten zugreift, sollten Sie davon ausgehen, dass alle Benutzereingaben böswillig sind, solange nicht das Gegenteil bewiesen ist. Andernfalls ist die Anwendung anfällig für Angriffe. Eine Art von möglichen Angriffen wird als „Einschleusung von SQL-Befehlen“ bezeichnet. Dabei wird böswilliger Code an Zeichenfolgen angefügt, die später an eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] übergeben und dann analysiert und ausgeführt werden. Zum Verhindern solcher Angriffe sollten Sie, wenn möglich, gespeicherte Prozeduren mit Parametern verwenden und Benutzereingaben immer überprüfen.

Das Überprüfen von Benutzereingaben im Clientcode ist wichtig, damit Sie keine Roundtrips zum Server verschwenden. Es ist von genauso großer Wichtigkeit, Parameter für gespeicherte Prozeduren auf dem Server zu überprüfen, um Eingaben abzufangen, die ungültig sind und die clientseitige Überprüfung umgehen.

Weitere Informationen zur Einschleusung von SQL-Befehlen und Möglichkeiten, dies zu verhindern, finden Sie unter „Einschleusung von SQL-Befehlen“ in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation. Weitere Informationen zum Überprüfen von Parametern für gespeicherte Prozeduren finden Sie unter „Gespeicherte Prozeduren ([!INCLUDE[ssDE](../../includes/ssde_md.md)])“ und den untergeordneten Themen in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.

## <a name="see-also"></a>Weitere Informationen

[Schützen von JDBC-Treiberanwendungen](../../connect/jdbc/securing-jdbc-driver-applications.md)
