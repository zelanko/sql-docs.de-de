---
title: Installieren von SSMA für SAP ASE (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/29/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 91a4dfcf8add3900c51e33a6e40fa874ce9f9798
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68028972"
---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>Installieren von SSMA für SAP ASE (sybasedesql)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant (SSMA) für SAP Adaptive Server Enterprise (ASE) besteht aus einer Client Anwendung, mit der Sie eine Migration von SAP ASE zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank durchführen. Außerdem enthält es ein Erweiterungspaket, das die Datenmigration und die Verwendung von ASE-Systemfunktionen in den migrierten Datenbanken unterstützt.  
  
Installieren Sie die Client Anwendung auf dem Computer, von dem aus Sie die Migrations Schritte ausführen möchten. Installieren Sie die Erweiterungspaket Dateien auf dem Computer, auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem ausgeführt wird, auf dem die migrierten Datenbanken gehostet werden sollen.  
  
## <a name="upgrading-ssma-for-sap-ase"></a>Aktualisieren von SSMA für SAP ASE  
Wenn Sie ein Upgrade auf eine höhere Version von SSMA für SAP ASE durchführen möchten, müssen Sie zunächst den-Client und das Server Erweiterungspaket deinstallieren. Installieren Sie dann die neuere Version.  
  
Wenn Sie ein Projekt aus einer früheren Version von SSMA für SAP ASE öffnen, fragt SSMA, ob Sie das Projekt in die neuere Version konvertieren möchten. Klicken Sie auf **Ja** , um mit dem Projekt in der neueren Version von SSMA zu arbeiten.  
  
## <a name="contents"></a>Contents  
  
|Artikel|BESCHREIBUNG|  
|---------|---------------|  
|[Installieren von SSMA für SAP ASE Client &#40;sybasedesql&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|Enthält Informationen und Anweisungen zum Installieren von SSMA für den SAP ASE-Client.|  
|[Installieren von SSMA-Komponenten auf SQL Server &#40;sybasedesql-&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|Enthält Informationen und Anweisungen zum Installieren des Erweiterungspakets auf Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Entfernen von SSMA für SAP ASE-Komponenten &#40;sybasedesql&#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|Enthält Anweisungen zum Deinstallieren des Client Programms und des Erweiterungspakets.|  
  
## <a name="see-also"></a>Weitere Informationen:  
[Migrieren von SAP ASE-Datenbanken zu SQL Server Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
