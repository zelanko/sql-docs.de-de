---
title: Schützen von JDBC-Treiberanwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 90724ec6-a9cb-43ef-903e-793f89410bc0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fd01462987ef425af32c8537f1fc99218d59e290
ms.sourcegitcommit: 54cfeb36c9caa51ec68fa8f4a1918e305db5e00a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219429"
---
# <a name="securing-jdbc-driver-applications"></a>Schützen von JDBC-Treiberanwendungen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Das Verbessern der Sicherheit einer [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-Anwendung beschränkt sich nicht allein auf das Vermeiden der häufigsten Programmierfehler. Eine Anwendung, die auf Daten zugreift, weist eine Vielzahl von möglichen Fehlern auf, die Angreifer ausnutzen können, um vertrauliche Daten abzurufen, zu ändern oder zu beschädigen. Es ist daher wichtig, alle Aspekte der Sicherheit zu kennen, von der Bedrohungsmodellierung während der Entwurfsphase der Anwendung bis zur endgültigen Bereitstellung und weiter bei der laufenden Wartung.  
  
In den Themen in diesem Abschnitt werden einige häufige Sicherheitsrisiken beschrieben, unter anderem Verbindungszeichenfolgen, das Überprüfen von Benutzereingaben und allgemeine Anwendungssicherheit.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
| Thema                                                                            | BESCHREIBUNG                                                                                                                                                           |
| -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Sichern von Verbindungszeichenfolgen](../../connect/jdbc/securing-connection-strings.md) | Beschreibt Verfahren zum Schützen von Informationen, mit denen eine Verbindung mit einer Datenquelle hergestellt wird.                                                                                    |
| [Überprüfen der Benutzereingabe](../../connect/jdbc/validating-user-input.md)             | Beschreibt Verfahren zum Überprüfen von Benutzereingaben.                                                                                                                          |
| [Anwendungssicherheit](../../connect/jdbc/application-security.md)               | Beschreibt die Verwendung von Java-Richtlinienberechtigungen zum Sichern einer JDBC-Treiberanwendung.                                                                                |
| [Verwenden von Verschlüsselung](../../connect/jdbc/using-ssl-encryption.md)               | Beschreibt das Herstellen eines sicheren Kommunikationskanals mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank mithilfe von Transport Layer Security (TLS), zuvor als Secure Sockets Layer (SSL) bezeichnet. |
| [FIPS-Modus](../../connect/jdbc/fips-mode.md)                                     | In diesem Artikel wird die Verwendung des JDBC-Treibers im FIPS-konformen Modus beschrieben.                                                                                                              |
  
## <a name="see-also"></a>Weitere Informationen  

 [Übersicht über den JDBC-Treiber](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
