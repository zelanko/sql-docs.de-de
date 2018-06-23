---
title: Erteilen von Verarbeitungsberechtigungen für die Datenbank | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 69ba952e-09ae-49a9-9297-00e32e8e89a8
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: c309ca3781bea3594c6d7e8d1b912730371635e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160820"
---
# <a name="granting-process-database-permissions"></a>Erteilen von Berechtigungen zum Verarbeiten von Datenbanken
  Nach dem Installieren einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verfügen alle Mitglieder der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Serveradministratorrolle in dieser Instanz über serverweite Berechtigungen, beliebige Tasks innerhalb der Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] auszuführen. Standardmäßig besitzen keine anderen Benutzer die Berechtigung, Objekte in der Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]zu verwalten oder anzuzeigen.  
  
 Ein Mitglied der Serveradministratorrolle kann Benutzern serverweiten Administratorzugriff gewähren, indem er sie als Mitglieder der Rolle hinzufügt. Ein Mitglied der Serveradministratorrolle kann Benutzern auch den Zugriff auf eingeschränktem Niveau erteilen, indem ihnen eingeschränkte oder vollständige Administrator- oder Zugriffsberechtigungen auf Datenbankebene erteilt werden. Eingeschränkte Administratorberechtigungen schließen Berechtigungen zum Verarbeiten oder Lesen von Definitionen auf Datenbank-, Cube- oder Dimensionsebene ein.  
  
 Im Rahmen der Tasks in diesem Thema definieren Sie die Process Database Objects-Sicherheitsrolle, die Mitgliedern der Rolle die Berechtigung erteilt, alle Datenbankobjekte zu verarbeiten, sie jedoch nicht berechtigt, Daten innerhalb der Datenbank anzuzeigen.  
  
## <a name="defining-a-process-database-objects-security-role"></a>Definieren der Process Database Objects-Sicherheitsrolle  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Rollen** und anschließend auf **Neue Rolle** , um den Rollen-Designer zu öffnen.  
  
2.  Aktivieren Sie das Kontrollkästchen **Datenbank verarbeiten** .  
  
3.  Ändern Sie im Fenster Eigenschaften die **Namen** Eigenschaft für die neue Rolle zum `Process Database Objects Role`.  
  
     ![Rollen-Designer](../../2014/tutorials/media/l10-security-1.png "Rollen-Designer")  
  
4.  Wechseln Sie zur Registerkarte **Mitgliedschaft** des Rollen-Designers, und klicken Sie auf **Hinzufügen**.  
  
5.  Geben Sie die Konten der Windows-Domänenbenutzer oder -Gruppen ein, die Mitglieder dieser Rolle sind. Klicken Sie auf **Namen überprüfen** , um die Kontoinformationen zu überprüfen, und anschließend auf **OK**.  
  
6.  Wechseln Sie zur Registerkarte **Cubes** des Rollen-Designers.  
  
     Mitglieder dieser Rolle sind berechtigt, diese Datenbank zu verarbeiten, können jedoch nicht auf die Daten im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube zugreifen und besitzen keinen lokalen Cube/Drillthrough-Zugriff, wie in der folgenden Abbildung dargestellt.  
  
     ![Cubes (Registerkarte) des Rollen-Designers](../../2014/tutorials/media/l10-security-2.png "Cubes (Registerkarte) des Rollen-Designers")  
  
7.  Wechseln Sie zur Registerkarte **Dimensionen** des Rollen-Designers.  
  
     Mitglieder dieser Rolle sind berechtigt, alle Dimensionsobjekte in dieser Datenbank zu verarbeiten und verfügen standardmäßig über Leseberechtigungen für jedes Dimensionsobjekt in der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Datenbank.  
  
8.  Klicken Sie im Menü **Erstellen** auf **Analysis Services Tutorial bereitstellen**.  
  
     Sie haben nun die Process Database Objects-Sicherheitsrolle erfolgreich definiert und bereitgestellt. Nach dem Bereitstellen eines Cubes in der Produktionsumgebung können die Administratoren des bereitgestellten Cubes nach Bedarf der Rolle Benutzer hinzufügen, um Verarbeitungsaufgaben an bestimmte Benutzer zu delegieren.  
  
> [!NOTE]  
>  Durch Herunterladen und Installieren der Beispiele ist für Lektion 10 ein abgeschlossenes Projekt verfügbar. Weitere Informationen finden Sie unter [Installieren von Beispieldaten und -projekten für das Analysis Services-Tutorial zur mehrdimensionalen Modellierung](install-sample-data-and-projects.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Rollen und Berechtigungen &#40;Analysis Services&#41;](multidimensional-models/roles-and-permissions-analysis-services.md)  
  
  