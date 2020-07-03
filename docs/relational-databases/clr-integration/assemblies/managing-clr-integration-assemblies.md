---
title: Verwalten von CLR-Integrationsassemblys Microsoft-Dokumentation
description: Sie können verwaltete DLL-Assemblys in SQL Server hosten.  Sie können Assemblys registrieren, ändern und löschen sowie zugehörige Dateien und Berechtigungen verwalten.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
author: rothja
ms.author: jroth
ms.openlocfilehash: 84f10e104754019e67255b1a031e228a9ff4c48e
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85899584"
---
# <a name="managing-clr-integration-assemblies"></a>Verwalten von CLR-Integrationsassemblys
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Verwalteter Code wird kompiliert und dann in Einheiten bereitgestellt, die Assembly genannt werden. Eine Assembly wird als DLL oder ausführbare Datei (EXE) gepackt. Während eine ausführbare Datei auch alleine ausgeführt werden kann, muss eine DLL in einer vorhandenen Anwendung gehostet werden. Verwaltete DLL-Assemblys können in geladen und von gehostet werden [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Bei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ist es erforderlich, die Assembly mit einer CREATE ASSEMBLY-Anweisung in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank zu registrieren, bevor sie in den Prozess geladen und verwendet werden kann. Assemblys können auch von einer neueren Version aus mithilfe der ALTER ASSEMBLY-Anweisung aktualisiert oder aus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mithilfe der DROP ASSEMBLY-Anweisung entfernt werden.  
  
 Assemblyinformationen werden in der **sys. assembly_files** -Tabelle in der Datenbank gespeichert, in der die Assembly installiert wurde. Die **sys. assembly_files** -Tabelle enthält die folgenden Spalten.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|assembly_id|Der für die Assembly definierte Bezeichner. Diese Nummer wird allen Objekten mit Bezug auf dieselbe Assembly zugewiesen.|  
|name|Der Name des Objekts.|  
|file_id|Eine Zahl, die die einzelnen-Objekte identifiziert, wobei das erste-Objekt, das einem angegebenen zugeordnet ist, **assembly_id** den Wert 1 erhält. Wenn mehrere Objekte mit demselben **assembly_id**verknüpft sind, wird jeder nachfolgende **file_id** Wert um 1 erhöht.|  
|Inhalt|Die Hexadezimaldarstellung der Assembly oder Datei.|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erstellen von Assemblys](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
 Erläutert das Erstellen der Assemblys SAFE, EXTERNAL_ACCESS und UNSAFE CLR in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Ändern einer Assembly](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)  
 Beschreibt das Aktualisieren von CLR-Assemblys in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Löschen von Assemblys](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)  
 Erläutert das Löschen von CLR-Assemblys aus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheit der CLR-Integration](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [CLR-Integration und Codezugriffssicherheit](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)  
  
  
