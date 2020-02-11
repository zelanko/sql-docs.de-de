---
title: Anfügen und trennen von Analysis Services Datenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: 4447f58baaa5ea88a48c67a9a32fcda77681d8d4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66077488"
---
# <a name="attach-and-detach-analysis-services-databases"></a>Anfügen und Trennen von Analysis Services-Datenbanken
  Es gibt häufig Situationen, in denen ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbankadministrator (DBA) eine Datenbank für eine bestimmte Zeit offline schalten und die Datenbank später auf derselben oder einer anderen Serverinstanz wieder online schalten möchte. Diese Situationen hängen in der Regel von Geschäftsforderungen ab, z. B. wenn die Datenbank zur Leistungssteigerung auf einen anderen Datenträger verschoben werden soll, wenn bei Datenbankzuwachs Platz geschaffen werden muss oder wenn ein Produkt aktualisiert werden soll. Für diese und weitere Fälle ermöglichen die Befehle `Attach` und `Detach` dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbankadministrator, die Datenbank mit wenig Aufwand offline und später wieder online zu schalten.  
  
## <a name="attach-and-detach-commands"></a>Die Befehle "Attach" und "Detach"  
 Mit dem `Attach`-Befehl können Sie eine Datenbank, die offline geschaltet wurde, wieder online schalten. Sie können die Datenbank an die ursprüngliche Serverinstanz oder eine andere Instanz anfügen. Wenn Sie eine Datenbank anfügen, kann der Benutzer die **ReadWriteMode** -Einstellung für die Datenbank angeben. Mit dem `Detach`-Befehl können Sie eine Datenbank vom Server offline schalten.  
  
## <a name="attach-and-detach-usage"></a>Verwendung der Befehle "Attach" und "Detach"  
 Der `Attach`-Befehl wird verwendet, um eine vorhandene Datenbankstruktur online zu schalten. Wenn die Datenbank im `ReadWrite`-Modus angefügt wird, kann sie nur einmal an eine Serverinstanz angefügt werden. Wird die Datenbank hingegen im `ReadOnly`-Modus angefügt, kann sie mehrfach an verschiedene Serverinstanzen angefügt werden. Die gleiche Datenbank kann jedoch nicht mehr als einmal an die gleiche Serverinstanz angefügt werden. Bei dem Versuch, die gleiche Datenbank mehr als einmal anzufügen, wird ein Fehler ausgegeben, auch wenn die Daten in separate Ordner kopiert wurden.  
  
> [!IMPORTANT]  
>  Wenn für das Trennen der Datenbank ein Kennwort erforderlich ist, ist für das Anfügen der Datenbank das gleiche Kennwort erforderlich.  
  
 Der `Detach`-Befehl wird verwendet, um eine vorhandene Datenbankstruktur offline zu schalten. Geben Sie beim Trennen einer Datenbank ein Kennwort an, um vertrauliche Metadaten zu schützen.  
  
> [!IMPORTANT]  
>  Verwenden Sie zum Schutz des Inhalts der Datendateien eine Zugriffssteuerungsliste für den Ordner, die Unterordner und die Datendateien.  
  
 Wenn Sie eine Datenbank trennen, führt der Server folgende Schritte aus.  
  
|Trennen einer Datenbank mit Lese-/Schreibzugriff|Trennen einer schreibgeschützten Datenbank|  
|--------------------------------------|-------------------------------------|  
|1) Der Server gibt eine Anforderung für eine CommitExclusive-Sperre für die Datenbank aus.<br />2) Der Server wartet, bis für alle laufenden Transaktionen ein Commit oder ein Rollback ausgeführt wird.<br />3) Der Server erstellt alle Metadaten, die zum Trennen der Datenbank erforderlich sind.<br />4) Die Datenbank wird als gelöscht markiert.<br />5) Der Server führt einen Commit für die Transaktion aus.|1) Die Datenbank wird als gelöscht markiert.<br />2) Der Server führt einen Commit für die Transaktion aus.<br /><br /> <br /><br /> Hinweis: Das Kennwort für die Trennung kann für eine schreibgeschützte Datenbank nicht geändert werden. Wenn der Kennwortparameter für eine angefügte Datenbank, die bereits ein Kennwort enthält, angegeben wird, wird ein Fehler ausgegeben.|  
  
 Die Befehle `Attach` und `Detach` müssen als einzelne Vorgänge ausgeführt werden. Sie können nicht in der gleichen Transaktion mit anderen Vorgängen kombiniert werden. Außerdem handelt es `Attach` sich `Detach` bei den Befehlen und um atomarische transaktionale Befehle. Dies bedeutet, dass der Vorgang entweder erfolgreich ist oder fehlschlägt. Keine Datenbank wird in einem unvollendeten Status belassen.  
  
> [!IMPORTANT]  
>  Zum Ausführen des `Detach`-Befehls sind Server- oder Datenbankadministratorberechtigungen erforderlich.  
  
> [!IMPORTANT]  
>  Zum Ausführen des `Attach`-Befehls sind Serveradministratorberechtigungen erforderlich.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Verschieben einer Analysis Services Datenbank](move-an-analysis-services-database.md)   
 [Datenbanklesemodusmodi](database-readwritemodes.md)   
 [Wechseln einer Analysis Services Datenbank zwischen Schreib geschütztem Modus und Lese-/Schreibmodus](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)   
 [Detach-Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element)   
 [Attach-Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)  
  
  
