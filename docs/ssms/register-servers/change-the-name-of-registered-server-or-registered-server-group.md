---
title: Ändern des Namens eines registrierten Servers oder einer Servergruppe
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 10e1546b-9edb-400c-8676-2ea1192d6134
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 08/02/2016
ms.openlocfilehash: cefef29e85ea4494faaa10385c45fc45a77a7e1e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75258896"
---
# <a name="change-the-name-of-registered-server-or-registered-server-group"></a>Ändern des Namens eines registrierten Servers oder einer Servergruppe

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

In diesem Thema wird beschrieben, wie Sie den Namen eines registrierten Servers oder einer Servergruppe mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ändern. Dieser Name kann jedoch jederzeit geändert werden. Bei einer Änderung des Namens eines registrierten Servers wird nur die Anzeige des Namens geändert. Um die Verbindung zu einem anderen Server herzustellen, müssen Sie die Verbindungseigenschaften des registrierten Servers bearbeiten.  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio

Navigieren Sie über das Menü zu **Ansicht\\Registrierte Server**, um den Bereich **Registrierte Server** zu öffnen.

### <a name="to-change-the-name-of-a-server"></a>So ändern Sie den Namen eines Servers

1. Erweitern Sie in **Registrierte Server**die Option **Datenbank-Engine** und anschließend **Lokale Servergruppen**.  

2. Klicken Sie mit der rechten Maustaste zum Auswählen auf **Eigenschaften** , um das Dialogfeld **Serverregistrierungseigenschaften bearbeiten** zu öffnen.

3. Geben Sie im Textfeld **Name des registrierten Servers** den neuen Namen für die Serverregistrierung ein, und klicken Sie anschließend auf **Speichern**.  

### <a name="to-change-the-name-of-a-server-group"></a>So ändern Sie den Namen einer Servergruppe  

1. Erweitern Sie in **Registrierte Server**die Option **Datenbank-Engine** und anschließend **Lokale Servergruppen**.  

2. Klicken Sie mit der rechten Maustaste auf eine Servergruppe, und wählen Sie **Eigenschaften** aus, um das Dialogfeld **Servergruppeneigenschaften bearbeiten** zu öffnen. 

3. Geben Sie im Textfeld **Gruppenname** den neuen Namen für die Servergruppe ein, und klicken Sie anschließend auf **Speichern**.  

## <a name="see-also"></a>Weitere Informationen

[Ändern der Registrierung eines Servers &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/change-a-server-s-registration-sql-server-management-studio.md)