---
title: Häufig gestellte Fragen (FAQ) zu ODBC (Linux und macOS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99b92271060cbe670b48058e988b104aa296474b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731528"
---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>Häufig gestellte Fragen (FAQ) zu ODBC (Linux und macOS)
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Im Folgenden finden Sie Antworten auf Fragen zum ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux und macOS.
  
## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

**Wie funktionieren die vorhandenen ODBC-Anwendungen unter Linux und macOS mit dem Treiber?**  
Sie sollten in der Lage sein, die ODBC-Anwendungen, die Sie unter Linux oder macOS mit anderen Treibern kompiliert und ausgeführt haben, zu kompilieren und auszuführen. 
  
**Welche Features von [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] werden von dieser Version des Treibers unterstützt?**

Der ODBC-Treiber unter Linux und macOS unterstützt mit Ausnahme von LocalDB alle Serverfeatures in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. Weitere Informationen zu von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützten Features finden Sie unter [Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
**Unterstützt der Treiber die Kerberos-Authentifizierung?**  
Ja. Wenn Sie einer vorhandenen Kerberos-Umgebung eingerichtet haben, Sie sollten möglicherweise für die Verbindung mit Servern, die mit der `Trusted_Connection=Yes` DSN- oder Verbindungszeichenfolge-String-Option. Weitere Informationen finden Sie unter [Using Integrated Authentication (Verwenden der integrierten Authentifizierung)](../../../connect/odbc/linux-mac/using-integrated-authentication.md).  
  
**Welche Unicode-Codierung sollte eine Anwendung verwenden?**  
UTF-8 für SQL_CHAR-Daten und UTF-16 für SQL_WCHAR-Daten.  

**Gibt es ODBC-Beispiele, die ich herunterladen und mit dem Treiber laufen lassen kann, um damit zu experimentieren oder sie auszuwerten?**

Ein Beispiel hierzu finden Sie unter [Vorhandene MSDN C++ ODBC-Beispiele für die ODBC-Treiber unter Linux](http://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) . Dies gilt auch für die MacOS-ODBC-Treiber. 

**Wird von der ODBC-Treiber unter Linux oder MacOS open-Source?**

Nein. die ODBC-Treiber unter Linux und MacOS sind nicht open Source-Produkt.  

## <a name="see-also"></a>Weitere Informationen finden Sie unter
[Installieren des Microsoft ODBC Driver for SQL Server unter Linux und macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
