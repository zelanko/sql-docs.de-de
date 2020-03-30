---
title: Abfragen von Spalten unter Verwendung von Always Encrypted mit Secure Enclaves | Microsoft-Dokumentation
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
ms.openlocfilehash: d0a522d6deb01169189d6f5faaf7ba2f189d1522
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "73595505"
---
# <a name="query-columns-using-always-encrypted-with-secure-enclaves"></a>Abfragen von Spalten mit Always Encrypted mit Secure Enclaves
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

In diesem Artikel werden allgemeine Überlegungen zum Ausführen von Abfragen für verschlüsselte Spalten mithilfe einer serverseitigen Secure Enclave für [Always Encrypted mit Secure Enclaves](always-encrypted-enclaves.md) beschrieben. 

Die folgenden Abfragetypen umfassen die Verwendung einer Secure Enclave:
- Abfragen, die direkte kryptografische Vorgänge mithilfe von Enclave-fähigen Schlüsseln auslösen. Weitere Informationen finden Sie unter [Direkte Konfiguration der Spaltenverschlüsselung mit Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md).
- *Umfangreiche Abfragen*: Bereichsvergleiche oder Musterabgleichsvorgänge für Spalten, die mithilfe von zufälliger Verschlüsselung und Enclave-fähigen Schlüsseln verschlüsselt wurden.
- Abfragen, die mithilfe der zufälligen Verschlüsselung und Enclave-fähigen Schlüsseln Indizes für Spalten erstellen oder aktualisieren. Weitere Informationen finden Sie unter [Erstellen und Verwenden von Indizes in Spalten mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-create-use-indexes.md).

> [!NOTE]
> Umfangreiche Abfragen und Indizes werden nur für Enclave-fähige Spalten (Spalten, die mit Enclave-fähigen Spaltenverschlüsselungsschlüssel verschlüsselt sind) unterstützt, die eine zufällige Verschlüsselung verwenden. Die deterministische Verschlüsselung bietet keine Unterstützung für umfangreiche Abfragen oder Indizes.

> [!NOTE]
> Umfangreiche Abfragen für verschlüsselte Zeichenfolgenspalten erfordern, dass die Spalten die Sortierungen mit einer binary2-Sortierreihenfolge (BIN2-Sortierungen) verwenden. 


## <a name="next-steps"></a>Nächste Schritte
- [Abfragen von Spalten unter Verwendung von Always Encrypted mit Secure Enclaves mit SSMS](always-encrypted-enclaves-query-columns-ssms.md)

## <a name="see-also"></a>Weitere Informationen
- [Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)

