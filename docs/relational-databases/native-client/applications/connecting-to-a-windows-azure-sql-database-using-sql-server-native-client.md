---
description: Herstellen einer Verbindung mit einer Azure SQL-Datenbank mithilfe von SQL Server Native Client
title: Herstellen einer Verbindung mit Azure SQL-Datenbank
ms.custom: ''
ms.date: 03/14/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9b5335f05060bf40431621dc3c45cfb11e22c914
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91868418"
---
# <a name="connecting-to-an-azure-sql-database-using-sql-server-native-client"></a>Herstellen einer Verbindung mit einer Azure SQL-Datenbank mithilfe von SQL Server Native Client
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Ein Beispiel für das Herstellen einer Verbindung mit einer [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] mithilfe von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client finden Sie unter [Entwicklung: Themen zur Vorgehensweise (Azure SQL-Datenbank)](/previous-versions/azure/ee621787(v=azure.100)).  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a>Bekannte Probleme beim Herstellen einer Verbindung mit einer SQL-Datenbank  
 Die folgenden bekannten Probleme können auftreten, wenn mithilfe von [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] Native Client eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hergestellt wird:  
  
-   Eine mithilfe von **SQLBrowseConnect** hergestellte Verbindung wird möglicherweise abgelehnt, wenn **SQLBrowseConnect** in mehreren Phasen verwendet wird.  Beispiel: Im ersten Aufruf wird der Treibername gesendet, im zweiten Aufruf werden Informationen zum Server und Anmeldeinformationen (Benutzer und Kennwort) gesendet, die Verbindung wird hergestellt, und im dritten Aufruf werden ein Datenbankname und eine Sprache gesendet.  Der dritte Aufruf bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client eine USE-Anweisung zum Wechseln von Datenbanken ausgibt. Die USE-Anweisung wird jedoch in [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]nicht unterstützt und generiert den folgenden Fehler:  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
