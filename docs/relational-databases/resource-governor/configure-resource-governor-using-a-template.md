---
title: Konfigurieren der Ressourcenkontrolle mit einer Vorlage | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, templates
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 2b26aba44ff43de115268dcafa5ecc51e3f13c02
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "72903949"
---
# <a name="configure-resource-governor-using-a-template"></a>Konfigurieren der Ressourcenkontrolle mit einer Vorlage
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Sie können die Ressourcenkontrolle mit einer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]bereitgestellten Vorlage konfigurieren.  
  
-   **Vorbereitungen:**  [Berechtigungen](#Permissions)  
  
-   **Erstellen einer Arbeitsauslastungsgruppe mit** [einer Vorlage](#ConfRGTemplate)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
 Gehen Sie wie folgt vor, um eine Vorlage zu öffnen und zu bearbeiten, mit der ein Ressourcenpool und eine Arbeitsauslastungsgruppe für diesen Pool erstellt werden. Darüber hinaus können Sie mit dieser Vorlage eine benutzerdefinierte Klassifizierungsfunktion erstellen, die neue Verbindungen entweder in die Standardgruppe oder in die von Ihnen erstellte Arbeitsauslastungsgruppe leitet.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen der Ressourcenkontrolle in der Vorlage erfordern die CONTROL SERVER-Berechtigung.  
  
##  <a name="configure-resource-governor-using-a-template"></a><a name="ConfRGTemplate"></a> Konfigurieren der Ressourcenkontrolle mit einer Vorlage  
 **So konfigurieren Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]im Menü **Ansicht** auf **Vorlagen-Explorer**.  
  
2.  Erweitern Sie unter **Vorlagen-Explorer**den Eintrag **Resource Governor**, und doppelklicken Sie auf **Resource Governor konfigurieren**.  
  
3.  Geben Sie unter **Verbindung mit Datenbank-Engine herstellen**die erforderlichen Informationen ein, und klicken Sie dann auf **OK**. Die Vorlage Configure Resource Governor.sql wird im Abfrage-Editor bereitgestellt. Verwenden Sie diese Vorlage, um einen Ressourcenpool, eine Arbeitsauslastungsgruppe und eine Klassifizierungsfunktion zu erstellen und zu konfigurieren.  
  
4.  Wenn Sie die Werte in der Vorlage ändern möchten, drücken Sie die Tastenkombination STRG+UMSCHALT+M. Geben Sie im Fenster **Werte für Vorlagenparameter angeben** die gewünschten Werte ein.  
  
5.  Klicken Sie auf **OK**, um die an der Vorlage vorgenommenen Änderungen zu speichern.  
  
6.  Klicken Sie auf **Ausführen**, um die Abfrage auszuführen.  

## <a name="see-also"></a>Weitere Informationen  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Aktivieren der Ressourcenkontrolle](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Ressourcenpool für die Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Arbeitsauslastungsgruppe der Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Klassifizierungsfunktion der Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [Anzeigen der Eigenschaften der Ressourcenkontrolle](../../relational-databases/resource-governor/view-resource-governor-properties.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
