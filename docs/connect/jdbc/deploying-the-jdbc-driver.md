---
title: Verwenden des JDBC-Treibers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3ad3508d-d9b1-47fb-a63b-21cdc3ed44e0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b688e5b014915578df5c56ec5e6af2fc8fe26b16
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66781974"
---
# <a name="deploying-the-jdbc-driver"></a>Bereitstellen des JDBC-Treibers
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Wenn Sie eine Anwendung bereitstellen, die [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] benötigt, müssen Sie den JDBC-Treiber zusammen mit der Anwendung verteilen. Im Gegensatz zu Windows Data Access Components (Windows DAC), einer Komponente des Windows-Betriebssystems, handelt es sich beim JDBC-Treiber um eine Komponente von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Es gibt zwei Möglichkeiten, um den JDBC-Treiber mit der Anwendung bereitzustellen. Eine Möglichkeit besteht darin, die JDBC-Treiberdateien in ein eigenes benutzerdefiniertes Installationspaket aufzunehmen. Die zweite Möglichkeit besteht darin, das JDBC-Installationspaket von Microsoft zu verwenden, das Sie im [Microsoft JDBC-Treiber für SQL Server Developer Center](https://go.microsoft.com/fwlink/?LinkId=70166) herunterladen können.  
  
 In den folgenden Abschnitten wird beschrieben, wie das JDBC-Installationspaket unter Windows- und UNIX-Betriebssystemen verwendet wird.  
  
> [!NOTE]  
>  Allgemeine Informationen zur Bereitstellung von Java-Anwendungen finden Sie auf der Java-Website.  
  
## <a name="deploying-the-jdbc-driver-on-windows-systems"></a>Bereitstellen des JDBC-Treibers auf Windows-Systemen  
 Wenn Sie den JDBC-Treiber auf Windows-Betriebssystemen bereitstellen, müssen Sie die ausführbare ZIP-Dateiversion des Installationspakets verwenden, das normalerweise `sqljdbc_<version>_<language>.exe` heißt.  
  
 Wenn die ausführbare ZIP-Datei automatisch ausgeführt werden soll, müssen Sie in der Befehlszeile oder in einer Batchdatei wie folgt die Befehlszeilenoption `/auto` verwenden:  
  
 `sqljdbc_<version>_<language>.exe /auto`  
  
> [!NOTE]  
>  Bei Angabe der Option `/auto` erfolgt die Installation nicht wirklich automatisch, da auf dem Bildschirm des Benutzers ein WinZip-Dialogfeld angezeigt wird. Es sind jedoch keine Benutzereingaben erforderlich, da das Dialogfeld nach Abschluss der Dekomprimierung automatisch geschlossen wird.  
  
## <a name="deploying-the-driver-on-unix-systems"></a>Bereitstellen des JDBC-Treibers auf UNIX-Systemen  
 Wenn Sie den JDBC-Treiber auf UNIX-Betriebssystemen bereitstellen, müssen Sie die GZIP-Dateiversion des Installationspakets verwenden, das normalerweise `sqljdbc_<version>_<language>.tar.gz` heißt.  
  
 Vor der Installation des JDBC-Treibers müssen ggf. die Dienstprogramme "gzip" und "tar" auf dem System des Benutzers installiert und die Ordner mit den ausführbaren Dateien für die Dienstprogramme zur Umgebungsvariablen PATH hinzugefügt werden.  
  
 Navigieren Sie zum Entpacken der komprimierten TAR-Datei zu dem Verzeichnis, in das der Treiber entpackt werden soll, und geben Sie den folgenden Befehl ein:  
  
 `gzip -d sqljdbc_<version>_<language>.tar.gz`  
  
 Verschieben Sie die TAR-Datei zum Entpacken zu dem Verzeichnis, in dem der Treiber installiert werden soll, und geben Sie den folgenden Befehl ein:  
  
 `tar -xf sqljdbc_<version>_<language>.tar`  
  
## <a name="see-also"></a>Weitere Informationen  
 [Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
