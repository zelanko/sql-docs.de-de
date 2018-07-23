---
title: Installieren von SQL Server Data Tools | Microsoft-Dokumentation
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.package.stub
ms.assetid: 6f8616cb-9119-42c3-a9b1-936e088763e7
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2df3214ce5ae02e4feb076f77e66b153c4d2abdb
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088022"
---
# <a name="install-sql-server-data-tools"></a>Installieren von SQL Server Data Tools
In diesem Thema wird die Installation von SQL Server Data Tools beschrieben. Updates auf SQL Server Data Tools stehen auf der SQL Server Data Tools-Downloadseite ([Herunterladen und Installieren von SQL Server Data Tools (SSDT) für Visual Studio](http://go.microsoft.com/fwlink/?LinkID=616714)) zur Verfügung.  
  
Sowohl für Visual Studio 2013 als auch für Visual Studio 2012 sollten Sie immer die neuesten SQL Server Data Tools-Updates installieren, um Zugriff auf die neuesten Funktionen zu erhalten.  
  
## <a name="sql-server-data-tools-for-visual-studio-2013"></a>SQL Server Data Tools für Visual Studio 2013  
SQL Server Data Tools ist in Visual Studio 2013 Express für Web, Visual Studio 2013 Express für Desktop, Visual Studio Community 2013 und allen kostenpflichtigen SKUs enthalten, einschließlich der Professional-SKU und höherer Editionen. Nach der Installation von Visual Studio 2013 können Sie zu „Tools“ -> „Erweiterungen und Updates“ -> „Updates“ navigieren, um zu erfahren, ob Updates zur Installation bereit sind.  
  
## <a name="sql-server-data-tools-for-visual-studio-2012"></a>SQL Server Data Tools für Visual Studio 2012  
SQL Server Data Tools wird mit der SKU „Professional“ oder mit einer höheren SKU in Visual Studio 2012 ausgeliefert. Nachdem Sie Visual Studio 2012 und das SQL Server Data Tools-Update von November 2012 oder höher installiert haben, kann SQL Server Data Tools melden, wenn ein Update zur Installation bereitsteht. Weitere Informationen finden Sie unter [Dialogfeld „Nach Updates suchen“](../ssdt/check-for-updates-dialog-box.md).  
  
Wenn Visual Studio 2012 nicht installiert ist, installiert SQL Server Data Tools die integrierte Shell von Visual Studio 2012 und SQL Server Data Tools.  
  
## <a name="administrative-installation-point"></a>Administratorinstallationspunkt  
Wenn Sie SQL Server Data Tools auf mehreren Computern oder auf Computern ohne Internetzugriff installieren müssen, können Sie ein Administratorinstallationslayout auf einer Netzwerkfreigabe oder einem physischen Medium erstellen und den Installationsvorgang von diesem Installationspunkt ausführen.  
  
Um ein Installationslayout zu erstellen, laden Sie SSDTSetup.EXE herunter und führen die Datei mit der `/layout`*location* -Option aus, um ein Layout unter *Speicherort*zu erstellen. Anschließend können die Benutzer „SSDTSetup.Exe“ von *Speicherort*aus ausführen.  
  
Laden Sie "SSDTSetup.exe" herunter, indem Sie zu [Installieren der aktuellen SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=616714)navigieren, auf den Link für Ihre Visual Studio-Version klicken und dann "SSDTSetup.exe" für Ihre Sprache herunterladen.  
  
