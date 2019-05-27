---
title: Speichern einer Kopie eines Pakets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 21482a20-e420-4452-b7eb-8f9fa1929f31
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bdd8754ac3d4a63e038218c054d064f20485344b
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66056267"
---
# <a name="save-a-copy-of-a-package"></a>Speichern einer Kopie eines Pakets
  In diesem Verfahren wird beschrieben, wie Sie eine Kopie eines Pakets im Dateisystem, im Paketspeicher oder in der **msdb** -Datenbank in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]speichern. Wenn Sie einen Speicherort zum Speichern der Paketkopie angeben, können Sie auch den Namen des Pakets aktualisieren.  
  
 Der Paketspeicher kann sowohl die **msdb** -Datenbank als auch die Ordner im Dateisystem, nur **msdb**oder nur Ordner im Dateisystem einschließen. In **msdb**werden Pakete in der **sysssispackages** -Tabelle gespeichert. Diese Tabelle schließt eine **folderid** -Spalte ein, die den logischen Ordner identifiziert, zu dem das Paket gehört. Logische Ordner bieten eine gute Möglichkeit, gespeicherter Pakete in **msdb** auf die gleiche Weise zu gruppieren, in der Ordner im Dateisystem das Gruppieren von im Dateisystem gespeicherten Paketen ermöglichen. Zeilen in der **sysssispackagefolders** -Tabelle in **msdb** definieren die Ordner.  
  
 Wenn **msdb** nicht als Teil des Paketspeichers definiert ist, können Sie Pakete weiterhin vorhandenen logischen Ordnern zuordnen, wenn Sie SQL Server in der Option **Paketpfad** auswählen.  
  
> [!NOTE]  
>  Das Paket muss im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer geöffnet sein, damit Sie eine Kopie des Pakets speichern können.  
  
### <a name="to-save-a-copy-of-a-package"></a>So speichern Sie eine Kopie eines Pakets  
  
1.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, von dem Sie eine Kopie speichern möchten.  
  
2.  Klicken Sie im Menü **Datei** auf **Kopie von \<Paketdatei> speichern unter**.  
  
3.  Wählen Sie im Dialogfeld **Kopie des Pakets speichern** in der Liste **Paketspeicherort** einen Paketspeicherort aus.  
  
4.  Falls der Speicherort **SQL Server** oder **SSIS-Paketspeicher**ist, stellen Sie einen Servernamen bereit.  
  
5.  Wenn Sie in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]speichern, geben Sie den Authentifizierungstyp an und, falls Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung verwenden, einen Benutzernamen und ein Kennwort.  
  
6.  Geben Sie zum Angeben des Paketpfads entweder den Pfad ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen **(...)**, um den Speicherort des Pakets anzugeben. Der Standardname des Pakets lautet Paket. Optional können Sie den Paktnamen aktualisieren, sodass er Ihren Bedürfnissen entspricht.  
  
     Wenn Sie **SQL Server** in der Option **Paketpfad** auswählen, besteht der Paketpfad aus logischen Ordnern in **msdb** und dem Paketnamen. Ist z.B. das Paket DownloadMonthlyData dem Ordner Finance im Ordner MSDB (der Standardname des logischen Stammordners in **msdb**) zugeordnet, lautet der Paketpfad MSDB/Finance/DownloadMonthlyData für das Paket DownloadMonthlyData.  
  
     Wenn Sie **SSIS-Paketspeicher** in der Option **Paketpfad** auswählen, besteht der Paketpfad aus dem Ordner, der vom Integration Services-Dienst verwaltet wird. Befindet sich z. B. das Paket UpdateDeductions im Ordner HumanResources im Dateisystemordner, der von dem Dienst verwaltet wird, lautet der Paketpfad /File System/HumanResources/UpdateDeductions. Ist das Paket PostResumes dem Ordner HumanResources im Ordner MSDB zugeordnet, lautet der Paketpfad MSDB/HumanResources/PostResumes.  
  
     Wenn Sie **Dateisystem** in der Option **Paketpfad** auswählen, setzt sich der Paketpfad aus dem Speicherort im Dateisystem und dem Dateinamen zusammen. Ist z. B. der Paketname UpdateDemographics, lautet der Paketpfad C:\HumanResources\Quarterly\UpdateDemographics.dtsx.  
  
7.  Überprüfen Sie die Paketschutzebene.  
  
8.  Klicken Sie optional auf die Auslassungspunkte **(…)** neben dem Feld **Schutzebene**, um die Schutzebene zu ändern.  
  
    -   Wählen Sie im Dialogfeld **Paketschutzebene** eine andere Schutzebene aus.  
  
    -   Klicken Sie auf **OK**.  
  
9. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Pakete &#40;SSIS&#41;](../../2014/integration-services/integration-services-ssis-packages.md)   
 [Konfigurieren der Integration Services-Dienst &#40;SSIS-Dienst&#41;](service/integration-services-service-ssis-service.md)  
  
  
