---
title: Bereitstellen des JDBC-Treibers
ms.custom: ''
ms.date: 03/13/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3ad3508d-d9b1-47fb-a63b-21cdc3ed44e0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d7e66360e08646a623aec5ed6f0b0f92d6ac62bf
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "79433797"
---
# <a name="deploying-the-jdbc-driver"></a>Bereitstellen des JDBC-Treibers

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Wenn Sie eine Anwendung bereitstellen, die [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] benötigt, müssen Sie den JDBC-Treiber zusammen mit der Anwendung verteilen. Im Gegensatz zu Windows Data Access Components (Windows DAC), einer Komponente des Windows-Betriebssystems, handelt es sich beim JDBC-Treiber um eine Komponente von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Es gibt zwei Möglichkeiten, um den JDBC-Treiber mit der Anwendung bereitzustellen. Eine Möglichkeit besteht darin, die JDBC-Treiberdateien in ein eigenes benutzerdefiniertes Installationspaket aufzunehmen. Die zweite Möglichkeit besteht darin, das JDBC-Installationspaket von Microsoft zu verwenden, das Sie auf der [Downloadseite des Microsoft JDBC-Treibers für SQL Server](download-microsoft-jdbc-driver-for-sql-server.md) herunterladen können.  
  
In den folgenden Abschnitten wird beschrieben, wie das JDBC-Installationspaket unter Windows- und UNIX-Betriebssystemen verwendet wird.  
  
> [!NOTE]  
> Allgemeine Informationen zur Bereitstellung von Java-Anwendungen finden Sie auf der Java-Website.  
  
## <a name="deploying-the-jdbc-driver-on-windows-systems"></a>Bereitstellen des JDBC-Treibers auf Windows-Systemen

Wenn Sie den JDBC-Treiber auf Windows-Betriebssystemen bereitstellen, müssen Sie die ZIP-Dateiversion des Installationspakets entpacken, das normalerweise `sqljdbc_<version>_<language>.zip` heißt.

## <a name="deploying-the-driver-on-unix-systems"></a>Bereitstellen des JDBC-Treibers auf UNIX-Systemen

Wenn Sie den JDBC-Treiber auf UNIX-Betriebssystemen bereitstellen, müssen Sie die GZIP-Dateiversion des Installationspakets verwenden, das normalerweise `sqljdbc_<version>_<language>.tar.gz` heißt.  
  
Vor der Installation des JDBC-Treibers müssen ggf. die Dienstprogramme "gzip" und "tar" auf dem System des Benutzers installiert und die Ordner mit den ausführbaren Dateien für die Dienstprogramme zur Umgebungsvariablen PATH hinzugefügt werden.  
  
Navigieren Sie zum Entpacken der komprimierten TAR-Datei zu dem Verzeichnis, in das der Treiber entpackt werden soll, und geben Sie den folgenden Befehl ein:  
  
`gzip -d sqljdbc_<version>_<language>.tar.gz`  
  
Verschieben Sie die TAR-Datei zum Entpacken zu dem Verzeichnis, in dem der Treiber installiert werden soll, und geben Sie den folgenden Befehl ein:  
  
`tar -xf sqljdbc_<version>_<language>.tar`  

## <a name="legalities-of-driver-redistribution"></a>Rechtliche Informationen zur Weiterverteilung von Treibern

Die Versionen 6.0, 6.2, 6.4, 7.0, 7.2, 7.4 und 8.2 des JDBC-Treibers sind weitervertreibbar. Lesen Sie die Klausel _Verteilbarer Code_ in den jeweiligen Lizenzvereinbarungen.

Die JDBC-Treiberversionen 4.x sind veraltet. Die Unterstützung von 4.x wurde vor 2018 eingestellt.

## <a name="see-also"></a>Weitere Informationen

[Übersicht über den JDBC-Treiber](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
