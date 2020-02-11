---
title: Native Client-, Header-und Bibliotheksdateien
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- header files [SQL Server Native Client]
- SQLNCLI, header files
- OLE DB, header files
- library files [SQL Server Native Client]
- SQL Server Native Client, header files
- data access [SQL Server Native Client], header files
- SQL Server Native Client ODBC driver,header files
- data access [SQL Server Native Client], library files
- SQL Server Native Client, library files
- ODBC applications, header files
- SQLNCLI, library files
ms.assetid: 69889a98-7740-4667-aecd-adfc0b37f6f0
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fd697e0e1ab788413af5e35f9d947fc7e784759f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75258725"
---
# <a name="using-the-sql-server-native-client-header-and-library-files"></a>Verwenden der SQL Server Native Client-Header- und Bibliotheksdateien
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Header- und Bibliotheksdateien werden mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installiert. Es ist wichtig, beim Entwickeln von Anwendungen alle für die Entwicklung erforderlichen Dateien in die Entwicklungsumgebung zu kopieren. Weitere Informationen zum Installieren und erneuten verteilen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] von Native Client finden Sie unter [Installieren von SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md).  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Header- und -Bibliotheksdateien werden am folgenden Speicherort installiert:  
  
 *% Program Files%* \Microsoft SQL server\110\sdk  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Headerdatei (sqlncli.h) wird verwendet, um Ihren benutzerdefinierten Anwendungen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Datenzugriffsfunktionalitäten hinzuzufügen. Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Headerdatei enthält alle Definitionen, Attribute, Eigenschaften und Schnittstellen, die Sie mit den neuen, in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführten Funktionen nutzen können.  
  
 Zusätzlich zu der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Headerdatei steht die Bibliotheksdatei sqlncli11.lib zur Verfügung. Dabei handelt es sich um die Exportbibliothek für die Massenkopierfunktionalität ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Bulk Copy Program (BCP)) für ODBC.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Headerdatei ist abwärtskompatibel mit den mit Microsoft Data Access Components (MDAC) verwendeten Headerdateien sqloledb.h und odbcss.h, enthält aber weder die CLSIDs für SQLOLEDB (den in MDAC enthaltenen OLE DB-Anbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) noch die Symbole für die XML-Funktionalität. Letztere wird nicht von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt.  
  
 ODBC-Anwendungen können nicht im selben Programm auf den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Header (sqlncli.h) und odbcss.h verweisen. Auch wenn Sie keines der neuen, in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführten Funktionen verwenden, ist die Verwendung der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Headerdatei anstelle der älteren odbcss.h-Datei möglich.  
  
 OLE DB-Anwendungen, die den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verwenden, brauchen nur auf sqlncli.h zu verweisen. Wenn eine Anwendung MDAC (SQLOLEDB) und den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verwendet, kann sowohl auf sqloledb.h als auch auf sqlncli.h verwiesen werden, unter der Voraussetzung, dass sqloledb.h zuerst angegeben wird.  
  
## <a name="using-the-sql-server-native-client-header-file"></a>Verwenden der SQL Server Native Client-Headerdatei  
 Um die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Header Datei zu verwenden, müssen Sie eine **include** -Anweisung innerhalb des C/C++-Programmiercodes verwenden. In den folgenden Abschnitten wird beschrieben, wie Sie dies sowohl für OLE DB- als auch für ODBC-Anwendungen durchführen können.  
  
> [!NOTE]  
>  Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Header- und Bibliotheksdateien können nur mithilfe von Visual Studio C++ 2002 oder höher kompiliert werden.  
  
### <a name="ole-db"></a>OLE DB  
 Zum Verwenden der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Headerdatei in einer OLE DB-Anwendung geben Sie den folgenden Programmiercode ein:  
  
```  
#define _SQLNCLI_OLEDB_  
include "sqlncli.h";  
```  
  
> [!NOTE]  
>  Die erste der oben stehenden Codezeilen sollte weggelassen werden, wenn sowohl die OLE DB- als auch die ODBC-API von der Anwendung verwendet werden. Wenn die Anwendung außerdem eine **include** -Anweisung für sqloledb. h enthält, muss die **include** -Anweisung für sqlncli. h darauf folgen.  
  
 Verwenden Sie für das Erstellen einer Verbindung mit einer Datenquelle über [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client die Zeichenfolge "SQLNCLI11" als Anbietername.  
  
### <a name="odbc"></a>ODBC  
 Zum Verwenden der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Headerdatei in einer ODBC-Anwendung geben Sie den folgenden Programmiercode ein:  
  
```  
#define _SQLNCLI_ODBC_  
include "sqlncli.h";  
```  
  
> [!NOTE]  
>  Die erste Codezeile, die oben gezeigt wird, sollte weggelassen werden, wenn sowohl OLE DB-als auch ODBC-APIs von der Anwendung verwendet werden. Wenn die Anwendung über eine `#include`-Anweisung für odbcss.h verfügt, sollte diese entfernt werden.  
  
 Verwenden Sie für das Erstellen einer Verbindung mit einer Datenquelle über [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client die Zeichenfolge "SQL Server Native Client 11.0" als Treibernamen.  
  
## <a name="component-names-and-properties-by-version"></a>Komponentennamen und Eigenschaften nach Version  
  
|Eigenschaft|SQL Server Native Client<br /><br /> SQL Server 2005|SQL Server Native Client 10.0<br /><br /> SQL Server 2008|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]|MDAC|  
|--------------|--------------------------------------------------|-------------------------------------------------------|---------------------------------------------------------------|----------|  
|ODBC-Treibername|SQL Native Client|SQL Server Native Client 10.0|SQL Server Native Client 11.0|SQL Server|  
|ODBC-Headerdateiname|Sqlncli.h|Sqlncli.h|Sqlncli.h|Odbcss.h|  
|ODBC-Treiber-DLL|Sqlncli.dll|Sqlncl10.dll|Sqlncl11.dll|sqlsrv32.dll|  
|ODBC-Bibliotheksdatei für BCP-APIs|Sqlncli.lib|Sqlncli10.lib|Sqlncli11.lib|Odbcbcp.lib|  
|ODBC-DLL für BCP-APIs|Sqlncli.dll|Sqlncli10.dll|Sqlncli11.dll|Odbcbcp.dll|  
|OLE DB PROGID|SQLNCLI|SQLNCLI10|SQLNCLI11|SQLOLEDB|  
|OLE DB-Headerdateiname|Sqlncli.h|Sqlncli.h|Sqlncli.h|Sqloledb.h|  
|OLE DB-Anbieter-DLL|Sqlncli.dll|Sqlncli10.dll|Sqlncli11.dll|Sqloledb.dll|  
  
 Die Datei sqlncli.h unterstützt mehrere Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client über das Makro SQLNCLI_VER. Standardmäßig legt SQLNCLI_VER die neueste Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client fest. Um eine Anwendung zu erstellen, die sqlncli10.dll anstatt sqlncli11.dll verwendet, legen Sie SQLNCLI_VER auf 10 fest.  
  
## <a name="static-linking-and-bcp-functions"></a>Statische Verknüpfung und BCP-Funktionen  
 Wenn eine Anwendung BCP-Funktionen verwendet, muss in der Verbindungszeichenfolge der Treiber mit derselben Version angegeben werden, die mit der für die Anwendungskompilierung verwendeten Headerdatei und Bibliothek ausgeliefert wurde.  
  
 Wenn Sie beispielsweise eine Anwendung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client und der zugeordneten Bibliotheksdatei (sqlncli11.lib) und Headerdatei (sqlncli.h) aus \Programme\Microsoft SQL Server\110\SDK kompilieren, sollten Sie (als Beispiel wird ODBC verwendet) in der Verbindungszeichenfolge unbedingt "DRIVER={SQL Server Native Client 11.0}" angeben.  
  
 Weitere Informationen finden Sie unter Ausführen von [Massen Kopier Vorgängen](../../../relational-databases/native-client/features/performing-bulk-copy-operations.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
