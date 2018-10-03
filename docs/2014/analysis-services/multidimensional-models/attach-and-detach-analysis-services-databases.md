---
title: Anfügen und Trennen von Analysis Services-Datenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssms.detachdatabase.f1
- sql12.asvs.ssms.attachdatabase.f1
- sql12.asvs.ssmsimbi.AttachDatabase.f1
- sql12.asvs.ssmsimbi.DetachDatabase.f1
helpviewer_keywords:
- databases [Analysis Services], attach
- databases [Analysis Services], detach
ms.assetid: 41887413-2d47-49b8-8614-553cb799fb18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 44624d6e223c00d76142b2b0859e8b312647da9e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48186180"
---
# <a name="attach-and-detach-analysis-services-databases"></a>Anfügen und Trennen von Analysis Services-Datenbanken
  Es gibt häufig Situationen, in denen ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbankadministrator (DBA) eine Datenbank für eine bestimmte Zeit offline schalten und die Datenbank später auf derselben oder einer anderen Serverinstanz wieder online schalten möchte. Diese Situationen hängen in der Regel von Geschäftsforderungen ab, z. B. wenn die Datenbank zur Leistungssteigerung auf einen anderen Datenträger verschoben werden soll, wenn bei Datenbankzuwachs Platz geschaffen werden muss oder wenn ein Produkt aktualisiert werden soll. Für diese und weitere Fälle ermöglichen die Befehle `Attach` und `Detach` dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbankadministrator, die Datenbank mit wenig Aufwand offline und später wieder online zu schalten.  
  
## <a name="attach-and-detach-commands"></a>Die Befehle "Attach" und "Detach"  
 Die `Attach` Befehl können Sie eine Datenbank wieder online schalten, die offline geschaltet wurde. Sie können die Datenbank an die ursprüngliche Serverinstanz oder eine andere Instanz anfügen. Wenn Sie eine Datenbank anfügen, kann der Benutzer die **ReadWriteMode** -Einstellung für die Datenbank angeben. Mit dem `Detach`-Befehl können Sie eine Datenbank vom Server offline schalten.  
  
## <a name="attach-and-detach-usage"></a>Verwendung der Befehle "Attach" und "Detach"  
 Die `Attach` -Befehl verwendet, um eine vorhandene Datenbankstruktur online zu schalten. Wenn die Datenbank, im angefügt wird `ReadWrite` Modus möglich angefügten nur ein Mal mit einer Serverinstanz. Allerdings, wenn die Datenbank, im angefügt wird `ReadOnly` -Modus werden kann mehrere Male an verschiedene Serverinstanzen angefügt. Die gleiche Datenbank kann jedoch nicht mehr als einmal an die gleiche Serverinstanz angefügt werden. Bei dem Versuch, die gleiche Datenbank mehr als einmal anzufügen, wird ein Fehler ausgegeben, auch wenn die Daten in separate Ordner kopiert wurden.  
  
> [!IMPORTANT]  
>  Wenn für das Trennen der Datenbank ein Kennwort erforderlich ist, ist für das Anfügen der Datenbank das gleiche Kennwort erforderlich.  
  
 Die `Detach` -Befehl verwendet, um die Funktion eine vorhandene Datenbankstruktur offline geschaltet werden. Geben Sie beim Trennen einer Datenbank ein Kennwort an, um vertrauliche Metadaten zu schützen.  
  
> [!IMPORTANT]  
>  Verwenden Sie zum Schutz des Inhalts der Datendateien eine Zugriffssteuerungsliste für den Ordner, die Unterordner und die Datendateien.  
  
 Wenn Sie eine Datenbank trennen, führt der Server folgende Schritte aus.  
  
|Trennen einer Datenbank mit Lese-/Schreibzugriff|Trennen einer schreibgeschützten Datenbank|  
|--------------------------------------|-------------------------------------|  
|1) Der Server gibt eine Anforderung für eine CommitExclusive-Sperre für die Datenbank aus.<br />2) Der Server wartet, bis für alle laufenden Transaktionen ein Commit oder ein Rollback ausgeführt wird.<br />3) Der Server erstellt alle Metadaten, die zum Trennen der Datenbank erforderlich sind.<br />4) Die Datenbank wird als gelöscht markiert.<br />5) Der Server führt einen Commit für die Transaktion aus.|1) Die Datenbank wird als gelöscht markiert.<br />2) Der Server führt einen Commit für die Transaktion aus.<br /><br /> <br /><br /> Hinweis: Das Kennwort für die Trennung kann für eine schreibgeschützte Datenbank nicht geändert werden. Wenn der Kennwortparameter für eine angefügte Datenbank, die bereits ein Kennwort enthält, angegeben wird, wird ein Fehler ausgegeben.|  
  
 Die Befehle `Attach` und `Detach` müssen als einzelne Vorgänge ausgeführt werden. Sie können nicht in der gleichen Transaktion mit anderen Vorgängen kombiniert werden. Darüber hinaus die `Attach` und `Detach` Befehle sind unteilbare Transaktionsbefehle. Dies bedeutet, dass der Vorgang entweder erfolgreich ist oder fehlschlägt. Keine Datenbank wird in einem unvollendeten Status belassen.  
  
> [!IMPORTANT]  
>  Sind Server- oder Datenbankadministratorberechtigungen erforderlich, zum Ausführen der `Detach` Befehl.  
  
> [!IMPORTANT]  
>  Zum Ausführen des `Attach`-Befehls sind Serveradministratorberechtigungen erforderlich.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Verschieben einer Analysis Services-Datenbank](move-an-analysis-services-database.md)   
 [Datenbank-ReadWriteModes](database-readwritemodes.md)   
 [Umschalten einer Analysis Services-Datenbank zwischen Schreib-und Lesemodus](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)   
 [Detach-Element](../xmla/xml-elements-commands/detach-element.md)   
 [Attach-Element](../xmla/xml-elements-commands/attach-element.md)  
  
  
