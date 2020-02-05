---
title: Erweiterte Verbindungseigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4edfab68-7e68-45e8-a3f3-a0049ff7eb9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 70e8c3cbc08837bce7c3b8aa9afeb3222165996c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "71298916"
---
# <a name="advanced-connection-properties"></a>Erweiterte Verbindungseigenschaften

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Verwenden Sie das Dialogfeld **Erweiterte Verbindungseigenschaften** , um der Verbindungszeichenfolge weitere Verbindungsparameter hinzuzufügen.  
  
 Bei zusätzlichen Verbindungsparametern kann es sich um beliebige ODBC-Verbindungsparameter handeln, die von der verwendeten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankinstanz unterstützt werden.  
  
 Die über das Dialogfeld **Erweiterte Verbindungseigenschaften** angegebenen Parameter werden den Parametern hinzugefügt, die im Dialogfeld **Verbindung mit SQL Server herstellen** ausgewählt wurden.  
  
 Durch die letzte Instanz eines Parameters werden alle vorherigen Instanzen des Parameters überschrieben. Parameter, die mithilfe des Dialogfelds **Erweiterte Verbindungseigenschaften** hinzugefügt werden, orientieren sich an den Parametern, die im Dialogfeld **SQL Server-Verbindung** bereitgestellt werden, und ersetzen diese. Wenn im Dialogfeld **SQL Server-Verbindung** beispielsweise SERVER1 als Servername bereitgestellt wird und die Seite **Zusätzliche Verbindungsparameter** die Angabe ;SERVER=SERVER2 enthält, wird die Verbindung mit SERVER2 hergestellt.  
  
 Parameter, die über das Dialogfeld **Erweiterte Verbindungseigenschaften** hinzugefügt werden, werden im Nur-Text-Format übergeben.  
  
> [!IMPORTANT]  
>  Schließen Sie keine Anmeldeinformationen in das Dialogfeld **Erweiterte Verbindungseigenschaften** ein. Sie werden nicht verschlüsselt, wenn sie über das Netzwerk übergeben werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zugreifen auf die CDC Designer Console](../../integration-services/change-data-capture/access-the-cdc-designer-console.md)   
 [SQL Server-Verbindung für die Instanzerstellung](../../integration-services/change-data-capture/sql-server-connection-for-instance-creation.md)  
  
  
