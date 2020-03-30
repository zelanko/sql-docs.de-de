---
title: Abfragen von Spalten unter Verwendung von Always Encrypted mit Secure Enclaves mit SSMS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/31/2019
ms.reviewer: vanto
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 6bee04f4a794a503b89b73d4ef4a6a1cef897b4b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "73595595"
---
# <a name="query-columns-using-always-encrypted-with-secure-enclaves-with-ssms"></a>Abfragen von Spalten unter Verwendung von Always Encrypted mit Secure Enclaves mit SSMS
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

In diesem Artikel wird beschrieben, wie SQL Server Management Studio zum Ausgeben von Abfragen verwendet wird, die eine serverseitige Secure Enclave für [Always Encrypted mit Secure Enclaves](always-encrypted-enclaves.md) verwenden. Dazu gehören:
- Abfragen, die direkt kryptografische Vorgänge auslösen
- Abfragen, die umfangreiche Berechnungen auslösen einschließlich Bereichsvergleiche oder Musterabgleichsvorgänge für Spalten, die mit Enclave-fähigen Schlüsseln verschlüsselt wurden
- Abfragen, die mithilfe der zufälligen Verschlüsselung und Enclave-fähigen Schlüsseln Indizes für Spalten erstellen oder aktualisieren.  

Befolgen Sie die Anweisungen im Artikel [Abfragen von Spalten mithilfe von Always Encrypted mit SQL Server Management Studio](always-encrypted-query-columns-ssms.md), um SSMS zum Ausführen von Abfragen für verschlüsselte Spalten mithilfe von Secure Enclave zu verwenden. Hier sind einige Punkte aufgeführt, die für Enclaves spezifisch sind und die Sie kennen sollten:

- Sie benötigen SSMS-Version 18.3 oder höher.
- Stellen Sie sicher, dass Sie Abfragen in einem Abfragefenster ausführen, indem Sie Secure Enclave von einer Verbindung verwenden, für die Always Encrypted und Enclave-Berechnungen aktiviert sind. Ausführliche Anweisungen dazu finden Sie unter [Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md) und [Aktivieren und Deaktivieren von Always Encrypted für eine Datenbankverbindung](always-encrypted-query-columns-ssms.md#en-dis).

## <a name="next-steps"></a>Nächste Schritte
- [Entwickeln von Anwendungen mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-client-development.md)

## <a name="see-also"></a>Weitere Informationen  
- [Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)
- [Direkte Konfiguration der Spaltenverschlüsselung mit Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md)
- [Erstellen und Verwenden von Indizes in Spalten mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-create-use-indexes.md)

