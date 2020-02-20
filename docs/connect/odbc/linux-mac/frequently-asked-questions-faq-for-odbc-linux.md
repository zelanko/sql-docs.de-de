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
ms.openlocfilehash: cc31a8ae385f2dbb28db30b299377ab5b38058f9
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68702771"
---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>Häufig gestellte Fragen (FAQ) zu ODBC unter Linux und macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Im Folgenden finden Sie Antworten auf Fragen zum ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux und macOS.
  
## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

**Wie funktionieren die vorhandenen ODBC-Anwendungen unter Linux und macOS mit dem Treiber?**  
Sie sollten in der Lage sein, die ODBC-Anwendungen, die Sie unter Linux oder macOS mit anderen Treibern kompiliert und ausgeführt haben, zu kompilieren und auszuführen. 
  
**Welche Features von [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] werden von dieser Version des Treibers unterstützt?**

Der ODBC-Treiber unter Linux und macOS unterstützt mit Ausnahme von LocalDB alle Serverfeatures in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. Weitere Informationen zu von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützten Features finden Sie unter [Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
**Unterstützt der Treiber die Kerberos-Authentifizierung?**  
Ja. Wenn Sie über eine Kerberos-Umgebung verfügen, sollten Sie mit dem `Trusted_Connection=Yes`-Datenquellennamen oder der -Verbindungszeichenfolgenoption eine Verbindung mit Servern herstellen können. Weitere Informationen finden Sie unter [Using Integrated Authentication (Verwenden der integrierten Authentifizierung)](../../../connect/odbc/linux-mac/using-integrated-authentication.md).  
  
**Welche Unicode-Codierung sollte eine Anwendung verwenden?**  
UTF-8 für SQL_CHAR-Daten und UTF-16 für SQL_WCHAR-Daten. Abhängig vom Gebietsschema des Systems und der Treiberversion werden möglicherweise auch Daten in anderen Codierungen als der UTF-8-Codierung unterstützt. Weitere Informationen finden Sie in den [Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md).

**Gibt es ODBC-Beispiele, die ich herunterladen und mit dem Treiber laufen lassen kann, um damit zu experimentieren oder sie auszuwerten?**

Ein Beispiel hierzu finden Sie unter [Vorhandene MSDN C++ ODBC-Beispiele für die ODBC-Treiber unter Linux](https://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) . Dies gilt auch für den ODBC-Treiber unter macOS. 

**Ist der ODBC-Treiber unter Linux oder macOS Open Source?**

Nein, der ODBC-Treiber unter Linux und macOS ist kein Open-Source-Produkt.  

## <a name="see-also"></a>Weitere Informationen
[Installieren des Microsoft ODBC Driver for SQL Server unter Linux und macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
