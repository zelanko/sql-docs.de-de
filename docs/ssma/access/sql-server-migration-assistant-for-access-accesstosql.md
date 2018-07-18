---
title: SQL Server Migration Assistant für Access (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 08/14/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 40c1eb02-26b2-44ba-969d-6c430c61c281
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 3ffc062101434178ba5739c553508202d6b73c6a
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985602"
---
# <a name="sql-server-migration-assistant-for-access-accesstosql"></a>SQL Server Migration Assistant für Access (AccessToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) für den Zugriff ist ein Tool zum Migrieren von Datenbanken von [!INCLUDE[msCoName](../../includes/msconame_md.md)] Zugriff auf die Versionen 97 bis 2010 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2017 unter Windows und Linux (Vorschau) / [!INCLUDE[msCoName](../../includes/msconame_md.md)] Azure SQL-Datenbank. SSMA für Access konvertiert, den Zugriff auf Datenbankobjekte zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder Azure SQL-Datenbank-Objekte, lädt die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder Azure SQL-Code, und klicken Sie dann Daten von den Zugriff auf migriert [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder Azure SQL.  
  
Diese Dokumentation führt Sie in SSMA für Access und enthält detaillierte Anweisungen zum Migrieren von Access-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure und Informationen zu Problemen, die nach der Migration auftreten können.  
  
## <a name="contents"></a>Inhalt  
  
|Abschnitt|Description|  
|-----------|---------------|  
|[What's New in SSMA for Access (Neuerungen in SSMA für Access)](http://msdn.microsoft.com/a24d3fc0-6911-4bfa-828a-197abf222e02)|Werden die Änderungen an der SSMA-Versionen aufgeführt.|  
|[Installieren von SQL Server Migration Assistant für Access](http://msdn.microsoft.com/dd50eebd-75df-4e0d-8c4d-88b511aae4c7)|Listet die Voraussetzungen zum Installieren von SSMA das Verfahren zum Installieren und lizenzieren SSMA und einen Link auf die neueste Version.|  
|[Erste Schritte mit SQL Server Migration Assistant für Access &#40;AccessToSQL&#41;](../../ssma/access/getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)|Führt SSMA und seine Benutzeroberfläche.|  
|[Access-Datenbanken vorbereitet für die Migration.](http://msdn.microsoft.com/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)|Beschreibt, wie Sie die Access-Datenbanken für die Konvertierung in Vorbereiten [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SQL Azure.|  
|[Migrieren von Access-Datenbanken zu SQLServer](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)|Bietet eine Übersicht über die Konvertierung und detaillierte Informationen zu jedem Schritt im Prozess an.|  
|[Verknüpfen den Zugriff auf Anwendungen mit SQLServer](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4)|Beschreibt, wie die vorhandenen Access-Anwendungen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[User Interface Reference (Verweis auf die Benutzeroberfläche)](http://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)|Enthält die Dokumentation für SSMA-Dialogfelder.|  
|[Working with SSMA for Access Console (Arbeiten mit SSMA für die Access-Konsole)](http://msdn.microsoft.com/ef94e843-9f88-45a2-86c4-a0af268738c4)|Enthält Dokumentation, in der SSMA-Konsolenanwendung|  
|[Informationsquellen für SSMA für Access](http://go.microsoft.com/fwlink/?LinkID=708538&clcid=0x409)|Enthält Informationen über die zusätzliche Informationsquellen.|  
  
