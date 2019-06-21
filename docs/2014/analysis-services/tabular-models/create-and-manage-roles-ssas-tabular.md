---
title: Erstellen und Verwalten von Rollen (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.rolemanager.f1
- sql12.asvs.bidtoolset.roledb.f1
ms.assetid: e23d27a8-e968-4082-9dbe-963fc724b5d9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 10e5e26142cd1819e4f2c5f884af9c2f2af10812
ms.sourcegitcommit: 0818f6cc435519699866db07c49133488af323f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67284905"
---
# <a name="create-and-manage-roles-ssas-tabular"></a>Erstellen und Verwalten von Rollen (SSAS – tabellarisch)
  Mit Rollen werden in tabellarischen Modellen Elementberechtigungen für ein Modell definiert. Rollen für ein Modellprojekt werden in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]im Dialogfeld Rollen-Manager definiert. Nach der Bereitstellung eines Modells können die Rollen vom Datenbankadministrator in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]verwaltet werden.  
  
 In den Aufgaben in diesem Thema wird beschrieben, wie Rollen während der Modellerstellung mithilfe des Dialogfelds Rollen-Manager in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]erstellt und verwaltet werden. Informationen zum Verwalten von Rollen in einer bereitgestellten Modelldatenbank finden Sie unter [Rollen tabellarischer Modelle &#40;SSAS – tabellarisch&#41;](roles-ssas-tabular.md).  
  
## <a name="tasks"></a>Richtlinienübersicht  
 Zum Erstellen, Bearbeiten, Kopieren und Löschen von Rollen verwenden Sie das Dialogfeld **Rollen-Manager** . Klicken Sie zum Anzeigen des Dialogfelds **Rollen-Manager** in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]auf das Menü **Modell** und anschließend auf **Rollen-Manager**.  
  
###  <a name="bkmk_new_role"></a> So erstellen Sie eine neue Rolle  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]auf das Menü **Modell** und dann auf **Rollen-Manager**.  
  
2.  Klicken Sie im Dialogfeld **Rollen-Manager** auf **Neu**.  
  
     Der Liste Rollen wird eine neue hervorgehobene Rolle hinzugefügt.  
  
3.  Geben Sie in der Liste **Rollen** im Feld **Name** einen Namen für die Rolle ein.  
  
     Der Name der Standardrolle wird für jede neue Rolle automatisch inkrementell erhöht. Es wird empfohlen, einen Namen einzugeben, durch den der Elementtyp eindeutig identifiziert wird, beispielsweise "Finance Managers" oder "Human Resources Specialists".  
  
4.  Klicken Sie im Feld **Berechtigungen** auf den Pfeil nach unten, und wählen Sie einen der folgenden Berechtigungstypen aus:  
  
    |Berechtigung|Beschreibung|  
    |----------------|-----------------|  
    |**Keine**|Mitglieder können keine Änderungen am Modellschema vornehmen und keine Daten abfragen.|  
    |**Lesen**|Mitglieder dürfen Daten (basierend auf Zeilenfiltern) abfragen, doch sie können keine Änderungen am Modellschema vornehmen.|  
    |**Lesen und verarbeiten**|Mitglieder können Daten (basierend auf Filtern auf Zeilenebene) abfragen und die Vorgänge Verarbeiten und Alles verarbeiten ausführen, jedoch keine Änderungen am Modellschema vornehmen.|  
    |**Verarbeiten**|Mitglieder können die Vorgänge Verarbeiten und Alles verarbeiten ausführen. Sie können weder das Modellschema ändern noch Daten abfragen.|  
    |**Administrator**|Mitglieder können Änderungen am Modellschema vornehmen und alle Daten abfragen.|  
  
5.  Um eine Beschreibung für die Rolle einzugeben, klicken Sie auf das Feld **Beschreibung** und geben dann eine Beschreibung ein.  
  
6.  Wenn die erstellte Rolle über Lese- bzw. Lese- und Verarbeitungsberechtigungen verfügt, können Sie Zeilenfilter mithilfe einer DAX-Formel hinzufügen. Um Zeilenfilter hinzuzufügen, klicken Sie auf die Registerkarte **Zeilenfilter** , wählen eine Tabelle aus, klicken auf das Feld **DAX-Filter** und geben eine DAX-Formel ein.  
  
7.  Um der Rolle Mitglieder hinzuzufügen, klicken Sie auf die Registerkarte **Mitglieder** und dann auf **Hinzufügen**.  
  
    > [!NOTE]  
    >  Rollenmitglieder können einem bereitgestellten Modell auch mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]hinzugefügt werden. Weitere Informationen finden Sie unter [Verwalten von Rollen mit SSMS &#40;SSAS – tabellarisch&#41;](manage-roles-by-using-ssms-ssas-tabular.md).  
  
8.  Geben Sie im Dialogfeld **Benutzer oder Gruppen auswählen** Windows-Benutzer- oder Windows-Gruppenobjekte als Mitglieder ein.  
  
9. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Rollen &#40;SSAS – tabellarisch&#41;](roles-ssas-tabular.md)   
 [Perspektiven &#40;SSAS – tabellarisch&#41;](perspectives-ssas-tabular.md)   
 [Analysieren in Excel &#40;SSAS – tabellarisch&#41;](analyze-in-excel-ssas-tabular.md)   
 [USERNAME-Funktion &#40;DAX&#41;](/dax/username-function-dax)   
 [CUSTOMDATA-Funktion &#40;DAX&#41;](/dax/customdata-function-dax)  
  
  
