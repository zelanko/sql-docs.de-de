---
title: Häufig gestellte Fragen (FAQ) zu ODBC (Linux und macOS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17d25f6084e136736dbc4c8a8ff3cb019ce4692e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37991372"
---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>Häufig gestellte Fragen (FAQ) zu ODBC (Linux und macOS)
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Im Folgenden finden Sie Antworten auf Fragen zum ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] unter Linux und macOS.
  
## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

**Wie funktionieren die vorhandenen ODBC-Anwendungen unter Linux und macOS mit dem Treiber?**  
Sie sollten in der Lage sein, die ODBC-Anwendungen, die Sie unter Linux oder macOS mit anderen Treibern kompiliert und ausgeführt haben, zu kompilieren und auszuführen. 
  
**Welche Features von [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] werden von dieser Version des Treibers unterstützt?**

Der ODBC-Treiber unter Linux und macOS unterstützt mit Ausnahme von LocalDB alle Serverfeatures in [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]. Weitere Informationen zu von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] unterstützten Features finden Sie unter [Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
**Unterstützt der Treiber die Kerberos-Authentifizierung?**  
Ja. Wenn Sie einer vorhandenen Kerberos-Umgebung eingerichtet haben, Sie sollten möglicherweise für die Verbindung mit Servern, die mit der `Trusted_Connection=Yes` DSN- oder Verbindungszeichenfolge-String-Option. Weitere Informationen finden Sie unter [Using Integrated Authentication (Verwenden der integrierten Authentifizierung)](../../../connect/odbc/linux-mac/using-integrated-authentication.md).  
  
**Welche Unicode-Codierung sollte eine Anwendung verwenden?**  
UTF-8 für SQL_CHAR-Daten und UTF-16 für SQL_WCHAR-Daten.  

**Gibt es ODBC-Beispiele, die ich herunterladen und mit dem Treiber laufen lassen kann, um damit zu experimentieren oder sie auszuwerten?**

Ein Beispiel hierzu finden Sie unter [Vorhandene MSDN C++ ODBC-Beispiele für die ODBC-Treiber unter Linux](http://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) . Dies gilt auch für die MacOS-ODBC-Treiber. 

Ist der ODBC-Treiber unter Linux Open Source?

Nein. die ODBC-Treiber unter Linux und MacOS sind nicht open Source-Produkt.  

## <a name="see-also"></a>Weitere Informationen finden Sie unter
[Installieren des Microsoft ODBC Driver for SQL Server unter Linux und macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
