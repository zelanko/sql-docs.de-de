---
title: Ändern des Namens eines registrierten Servers oder einer Servergruppe
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 10e1546b-9edb-400c-8676-2ea1192d6134
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 08/02/2016
ms.openlocfilehash: 32f59e2db98280a7d096e0f1f7d1a90895db010b
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86001787"
---
# <a name="change-the-name-of-registered-server-or-registered-server-group"></a>Ändern des Namens eines registrierten Servers oder einer Servergruppe

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

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