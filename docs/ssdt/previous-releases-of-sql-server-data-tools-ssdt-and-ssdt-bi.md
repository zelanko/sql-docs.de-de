---
title: Vorgängerversionen von SQL Server Data Tools (SSDT und SSDT-BI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/05/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssdt
ms.reviewer: ''
ms.suite: sql
ms.technology: ssdt
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5d32e301-0f44-4916-b0db-76e8322c0ab7
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 7d215d34425012573455fc5a8d4c5615fb1ea749
ms.sourcegitcommit: c929887686eabd6b754cf644a45656f0a0eb0445
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "43743433"
---
# <a name="previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi"></a>Vorgängerversionen von SQL Server Data Tools (SSDT und SSDT-BI)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
SQL Server Data Tools (SSDT) stellt Projektvorlagen und Entwurfsoberflächen zum Erstellen von SQL Server-Inhaltstypen bereit: relationale Datenbanken, Analysis Services-Modelle, Reporting Services-Berichte und Integration Services-Pakete.  
  
SSDT ist abwärtskompatibel, d.h., Sie können jederzeit [das neueste SSDT](download-sql-server-data-tools-ssdt.md) verwenden, um Datenbanken, Modelle, Berichte und Pakete zu entwerfen und bereitzustellen, die für ältere Versionen von SQL Server vorgesehen sind.  
  
> [!NOTE]  
> Die Visual Studio-Shell, mit der SQL Server-Inhaltstypen erstellt werden, wurde unter verschiedenen Namen veröffentlicht, etwa **SQL Server Data Tools**, **SQL Server Data Tools - Business Intelligence**und **Business Intelligence Development Studio**. Zum Lieferumfang von früheren Versionen gehörten unterschiedliche Sätze von Projektvorlagen. Möchten Sie alle Projektvorlagen zusammen in einem SSDT haben, benötigen Sie [die neueste Version](download-sql-server-data-tools-ssdt.md). Andernfalls müssen Sie wahrscheinlich mehrere frühere Versionen installieren, um alle Vorlagen zu erhalten, die in SQL Server verwendet werden.  Pro Version von Visual Studio ist nur eine Shell installiert. Wird ein zweites SSDT installiert, werden nur die fehlenden Vorlagen hinzugefügt.  

## <a name="recent-downloads"></a>Neueste Downloads

Die letzten Downloads werden für den unwahrscheinlichen Fall bereitgestellt, dass mit dem neuesten Release Probleme auftreten.

|SSDT-Release| Visual Studio 2017|
|:---|:---|
|15.7.1|[SSDT für VS2017 15.7.1](https://go.microsoft.com/fwlink/?LinkId=875613)|
|15.7.0|[SSDT für VS2017 15.7.0](https://go.microsoft.com/fwlink/?LinkId=874716)|
|15.6.0|[SSDT für VS2017 15.6.0](https://go.microsoft.com/fwlink/?LinkId=871368)|
<br>

|SSDT-Release| Visual Studio 2015|
|:---|:---|
|17.4|[SSDT für VS2015 17.4](https://go.microsoft.com/fwlink/?linkid=863440)|
|17.3|[SSDT für VS2015 17.3](https://go.microsoft.com/fwlink/?linkid=858660)|
|16.5|[SSDT für VS2015 16.5](https://go.microsoft.com/fwlink/?LinkID=832313)|  
<br>

|SSDT-Release| Visual Studio 2013|
|:---|:---|
|16.5|[SSDT für VS2013 16.5](https://go.microsoft.com/fwlink/?LinkID=832308)|  
<br>


\* SSDT unterstützt die letzten beiden Versionen von Visual Studio. SSDT für VS2013 wird mit dem Release von Visual Studio 2017 nicht mehr aktualisiert. Weitere Informationen finden Sie im Abschnitt *Häufig gestellte Fragen* dieses [Blogbeitrags des SSDT-Teams](https://blogs.msdn.microsoft.com/ssdt/2017/03/10/sql-server-data-tools-17-0-rc-and-ssdt-in-vs2017/).

  
## <a name="links-to-download-pages"></a>Links zu Downloadseiten 
**SQL Relational: Datenbank-Engine**  
  
Stellt Vorlagen bereit, mit denen relationale Datenbanken für das RDBMS und Azure SQL-Datenbank erstellt werden können. SSDT ist versionsunabhängig im Hinblick auf das Design einer relationalen Datenbank. Sie können Visual Studio 2012 oder 2013 mit jeder Version der SQL Server-Datenbank-Engine oder von Azure SQL-Datenbank verwenden.  
  
**Datenbank-Designer**  
  
-   [Herunterladen von SSDT für Visual Studio 2013](https://msdn.microsoft.com/dn864412)  
  
-   [Herunterladen von SSDT für Visual Studio 2012](https://msdn.microsoft.com/jj650015)  
  
-   **SSDT für Visual Studio 2010** ist nicht mehr verfügbar. Bitte wählen Sie eine neuere Version aus. Neuere Versionen von SSDT laufen parallel zu Ihren vorhandenen Installationen von Visual Studio 2010. SSDT muss nicht mit der Visual Studio-Vollversion übereinstimmen, die auf Ihrem Computer gespeichert ist.  
  
Visual Studio 2013-Kunden können eine Vorschauversion von SSDT herunterladen, um die neuen Funktionen zu testen, die es in der Produktversion noch nicht gibt.  
  
**SQL BI: Analysis Services, Reporting Services und Integration Services**  
  
BI-Vorlagen werden verwendet, um SSAS-Modelle, SSRS-Berichte und SSIS-Pakete zu erstellen. BI-Designer sind an bestimmte Versionen von SQL Server gebunden. Damit Sie die neueren BI-Funktionen nutzen können, installieren Sie den BI-Designer in einer neueren Version.  
  
**BI-Designer**  
  
[Herunterladen von SSDT-BI für Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=42313) (SQL Server 2014, SQL Server 2012, SQL Server 2008 und 2008 R2)  
  
[Herunterladen von SSDT-BI für Visual Studio 2012](https://www.microsoft.com/download/details.aspx?id=36843) (SQL Server 2014, SQL Server 2012, SQL Server 2008 und 2008 R2)  
  
Business Intelligence Development Studio (BIDS) wird über SQL Server-Setup installiert. Es gibt keinen Webdownload. (SQL Server 2008 und 2008 R2)  
  
Für SQL Server 2012 oder 2014 können Sie entweder **SSDT-BI für Visual Studio 2012** oder **SSDT-BI foder Visual Studio 2013**. Der einzige Unterschied zwischen den beiden besteht in der Visual Studio-Version.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Herunterladen von SQL Server Data Tools &#40;SSDT&#41;](../ssdt/download-sql-server-data-tools-ssdt.md)  
[Herunterladen von SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md)  
[SQL Tools and Utilities (Tools und Hilfsprogramme für SQL)](../tools/overview-sql-tools.md)
