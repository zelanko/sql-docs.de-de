---
title: Erweiterte Verbindungseigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4edfab68-7e68-45e8-a3f3-a0049ff7eb9e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 66681c42718e2c71e89eb673f30764af670ede73
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52770802"
---
# <a name="advanced-connection-properties"></a>Erweiterte Verbindungseigenschaften
  Verwenden Sie das Dialogfeld **Erweiterte Verbindungseigenschaften** , um der Verbindungszeichenfolge weitere Verbindungsparameter hinzuzufügen.  
  
 Bei zusätzlichen Verbindungsparametern kann es sich um beliebige ODBC-Verbindungsparameter handeln, die von der verwendeten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankinstanz unterstützt werden.  
  
 Die über das Dialogfeld **Erweiterte Verbindungseigenschaften** angegebenen Parameter werden den Parametern hinzugefügt, die im Dialogfeld **Verbindung mit SQL Server herstellen** ausgewählt wurden.  
  
 Durch die letzte Instanz eines Parameters werden alle vorherigen Instanzen des Parameters überschrieben. Parameter, die mithilfe des Dialogfelds **Erweiterte Verbindungseigenschaften** hinzugefügt werden, orientieren sich an den Parametern, die im Dialogfeld **SQL Server-Verbindung** bereitgestellt werden, und ersetzen diese. Wenn im Dialogfeld **SQL Server-Verbindung** beispielsweise SERVER1 als Servername bereitgestellt wird und die Seite **Zusätzliche Verbindungsparameter** die Angabe ;SERVER=SERVER2 enthält, wird die Verbindung mit SERVER2 hergestellt.  
  
 Parameter, die über das Dialogfeld **Erweiterte Verbindungseigenschaften** hinzugefügt werden, werden im Nur-Text-Format übergeben.  
  
> [!IMPORTANT]  
>  Schließen Sie keine Anmeldeinformationen in das Dialogfeld **Erweiterte Verbindungseigenschaften** ein. Sie werden nicht verschlüsselt, wenn sie über das Netzwerk übergeben werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf die CDC Designer Console](access-the-cdc-designer-console.md)   
 [SQL Server-Verbindung für die Instanzerstellung](sql-server-connection-for-instance-creation.md)  
  
  
