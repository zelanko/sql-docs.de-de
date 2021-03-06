---
title: Häufig gestellte Fragen (FAQ) zu ODBC unter Linux und macOS
description: Erhalten Sie Antworten zu häufig gestellten Fragen zu Microsoft ODBC Driver for SQL Server für Linux und macOS.
ms.custom: ''
ms.date: 05/06/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 700c89b520cdaa33a60f1adabe69c669388bcccb
ms.sourcegitcommit: fb1430aedbb91b55b92f07934e9b9bdfbbd2b0c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82886453"
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

Ein Beispiel hierzu finden Sie unter [Vorhandene MSDN C++ ODBC-Beispiele für die ODBC-Treiber unter Linux](/archive/blogs/sqlblog/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver) . Dies gilt auch für den ODBC-Treiber unter macOS.

**Ist der ODBC-Treiber unter Linux oder macOS Open Source?**

Nein, der ODBC-Treiber unter Linux und macOS ist kein Open-Source-Produkt.  

## <a name="see-also"></a>Weitere Informationen

- [Installieren von Microsoft ODBC Driver for SQL Server unter Linux](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Installieren von Microsoft ODBC Driver for SQL Server unter macOS](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md)
