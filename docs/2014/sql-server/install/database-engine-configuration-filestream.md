---
title: Datenbank-Engine-Konfiguration – Filestream | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], about FILESTREAM
ms.assetid: 641a10a1-ae52-4d26-8f1c-a032a4aeff02
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 190a6ce588ed40ab7cc9181476ca3730eeef34b5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63035629"
---
# <a name="database-engine-configuration---filestream"></a>Konfiguration der Datenbank-Engine - Filestream
  Verwenden Sie diese Seite, um FILESTREAM für diese Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zu aktivieren. FILESTREAM integriert die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in ein NTFS-Dateisystem gespeichert `varbinary(max)` binary large Object (BLOB)-Daten im Dateisystem. [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen können FILESTREAM-Daten eingefügt, aktualisiert, abgefragt, gesucht und gesichert werden. Die Win32-Dateisystemschnittstellen stellen Streamingzugriff auf die Daten bereit.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **FILESTREAM für Transact-SQL-Zugriff aktivieren**  
 Wählen Sie diese Option aus, um FILESTREAM für den [!INCLUDE[tsql](../../includes/tsql-md.md)] -Zugriff zu aktivieren. Dieses Steuerelement muss aktiviert werden, bevor die anderen Steuerelementoptionen verfügbar sind.  
  
 **FILESTREAM für E/A-Streamingzugriff auf Datei aktivieren**  
 Wählen Sie diese Option aus, um den Win32-Streamingzugriff für FILESTREAM zu aktivieren.  
  
 **Windows-Freigabename**  
 Verwenden Sie dieses Steuerelement, um den Namen der Windows-Freigabe einzugeben, in der die FILESTREAM-Daten gespeichert werden sollen.  
  
 **Streamingzugriff von Remoteclients auf FILESTREAM-Daten zulassen**  
 Aktivieren Sie dieses Steuerelement, damit Remoteclients auf diese FILESTREAM-Daten auf diesem Server zugreifen können.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren und Konfigurieren von FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
