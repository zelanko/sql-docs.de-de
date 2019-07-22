---
title: Validieren von Benutzereingaben | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8aa867b0-e6f0-49eb-93d3-817ae2ed8f77
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c2d890c4471dfeb85c1dd4f8f6f614a3b28cff90
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003897"
---
# <a name="validating-user-input"></a>Überprüfen der Benutzereingabe

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Wenn Sie eine Anwendung erstellen, die auf Daten zugreift, sollten Sie davon ausgehen, dass alle Benutzereingaben böswillig sind, solange nicht das Gegenteil bewiesen ist. Andernfalls ist die Anwendung anfällig für Angriffe. Eine Art von möglichen Angriffen wird als „Einschleusung von SQL-Befehlen“ bezeichnet. Dabei wird böswilliger Code an Zeichenfolgen angefügt, die später an eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] übergeben und dann analysiert und ausgeführt werden. Zum Verhindern solcher Angriffe sollten Sie, wenn möglich, gespeicherte Prozeduren mit Parametern verwenden und Benutzereingaben immer überprüfen.

Das Überprüfen von Benutzereingaben im Clientcode ist wichtig, damit Sie keine Roundtrips zum Server verschwenden. Es ist von genauso großer Wichtigkeit, Parameter für gespeicherte Prozeduren auf dem Server zu überprüfen, um Eingaben abzufangen, die ungültig sind und die clientseitige Überprüfung umgehen.

Weitere Informationen zur Einschleusung von SQL-Befehlen und Möglichkeiten, dies zu verhindern, finden Sie unter „Einschleusung von SQL-Befehlen“ in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation. Weitere Informationen zum Überprüfen von Parametern für gespeicherte Prozeduren finden Sie unter „Gespeicherte Prozeduren ([!INCLUDE[ssDE](../../includes/ssde_md.md)])“ und den untergeordneten Themen in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.

## <a name="see-also"></a>Weitere Informationen

[Sichern von JDBC-Treiberanwendungen](../../connect/jdbc/securing-jdbc-driver-applications.md)
