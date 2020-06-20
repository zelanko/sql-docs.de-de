---
title: Zugriff auf Dateien, die von Paketen verwendet werden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- packages [Integration Services], security
- configuration files [Integration Services]
- checkpoint files
- Integration Services packages, security
- logs [Integration Services], security
- files [Integration Services], security
- SQL Server Integration Services packages, security
ms.assetid: 2e3ddea9-5289-4289-a70e-11c018f34977
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 8f76636fa25b9a061f8e152c7df2eb583a386004
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84926529"
---
# <a name="access-to-files-used-by-packages"></a>Zugriff auf Dateien, die von Paketen verwendet werden
  Die Paketschutzebene bietet für Dateien, die außerhalb des Pakets gespeichert wurden, keinen Schutz. Hierzu gehören die folgenden Dateien:  
  
-   Konfigurationsdateien  
  
-   Prüfpunktdateien  
  
-   Protokolldateien  
  
 Diese Dateien müssen separat geschützt werden. Dies gilt insbesondere dann, wenn sie vertrauliche Informationen beinhalten.  
  
## <a name="configuration-files"></a>Konfigurationsdateien  
 Wenn in einer Konfiguration vertrauliche Informationen enthalten sind, wie z.B. der Anmeldename und das Kennwort, sollten Sie die Konfiguration in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]speichern oder eine Zugriffssteuerungsliste (ACL, Access Control List) verwenden, um den Zugriff auf den Speicherort bzw. auf den Ordner, in dem die Dateien gespeichert sind, zu beschränken und den Zugriff nur bestimmten Konten zu gewähren. In der Regel wird den Konten Zugriff gewährt, denen die Berechtigung zum Ausführen von Paketen erteilt wird, und den Konten, die Pakete verwalten und Probleme bei Paketen beheben. Hierzu gehört z. B. das Überprüfen der Inhalte der Konfiguration, des Prüfpunkts und der Protokolldateien. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bereitgestellte Speicher ist sicherer, da er Schutz auf Server- und Datenbankebene bietet. Verwenden Sie zum Speichern der Konfigurationen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurationstyp. Verwenden Sie zum Speichern im Dateisystem den XML-Konfigurationstyp.  
  
 Weitere Informationen finden Sie unter [Paketkonfigurationen](../../2014/integration-services/package-configurations.md), [Erstellen von Paketkonfigurationen](../../2014/integration-services/create-package-configurations.md)und [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
## <a name="checkpoint-files"></a>Prüfpunktdateien  
 Wenn die vom Paket verwendete Prüfpunktdatei vertrauliche Informationen enthält, sollten Sie entsprechend mithilfe einer Zugriffssteuerungsliste den Speicherort oder Ordner schützen, in dem Sie die Datei speichern. In Prüfpunktdateien werden aktuelle Statusinformationen zum Fortschritt des Pakets sowie die aktuellen Werte von Variablen gespeichert. Beispielsweise kann das Paket eine benutzerdefinierte Variable mit einer Telefonnummer enthalten. Weitere Informationen finden Sie unter [Neustarten von Paketen mit Prüfpunkten](packages/restart-packages-by-using-checkpoints.md).  
  
## <a name="log-files"></a>Protokolldateien  
 Protokolleinträge, die in das Dateisystem geschrieben werden, sollten ebenfalls mithilfe einer Zugriffssteuerungsliste geschützt werden. Protokolleinträge können auch in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Tabellen gespeichert und mithilfe der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Sicherheit geschützt werden. Protokolleinträge können vertrauliche Informationen enthalten. Angenommen, das Paket enthält einen Task SQL ausführen, mit dem eine SQL-Anweisung erstellt wird, die auf eine Telefonnummer verweist. In diesem Fall enthält der Protokolleintrag der SQL-Anweisung die Telefonnummer. Die SQL-Anweisung kann auch private Informationen zu Tabellen- und Spaltennamen in Datenbanken anzeigen. Weitere Informationen finden Sie unter [Integration Services-Protokollierung &#40;SSIS&#41;](performance/integration-services-ssis-logging.md).  
  
  
