---
title: Verwalten von Schlüsseln für Always Encrypted mit Secure Enclaves | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/30/2019
ms.reviewer: vanto
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: d3968c5c8f04cba8581dfdd44ac847f7010de994
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "73595625"
---
# <a name="manage-keys-for-always-encrypted-with-secure-enclaves"></a>Verwalten von Schlüsseln für Always Encrypted mit Secure Enclaves
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

[Always Encrypted mit Secure Enclaves](always-encrypted-enclaves.md) erweitert durch die Einführung von Enclave-fähigen Schlüsseln die Schlüsselverwaltung für [Always Encrypted](always-encrypted-database-engine.md): 

- **Enclave-fähiger Spaltenhauptschlüssel:** Ein Spaltenhauptschlüssel, der mit der im Spaltenhauptschlüssel-Metadatenobjekt in der Datenbank angegebenen `ENCLAVE_COMPUTATIONS`-Eigenschaft erstellt wird. 
- **Enclave-fähiger Spaltenverschlüsselungsschlüssel**: Ein Spaltenverschlüsselungsschlüssel, der mit einem Enclave-fähigen Spaltenhauptschlüssel verschlüsselt ist. Nur Enclave-fähige Spaltenverschlüsselungsschlüssel können für Berechnungen innerhalb einer serverseitigen Secure Enclave verwendet werden. 

Die allgemeinen Richtlinien und Prozesse für die [Verwaltung von Always Encrypted-Schlüsseln](overview-of-key-management-for-always-encrypted.md) gelten für die Verwaltung von Enclave-fähigen Schlüsseln. 

## <a name="managing-keys"></a>Verwalten von Schlüsseln

In den folgenden Artikeln werden die Aspekte erläutert, die zum Verwalten von Enclave-fähigen Schlüsseln spezifisch sind.

- [Bereitstellen Enclave-fähiger Schlüssel](always-encrypted-enclaves-provision-keys.md)
- [Rotieren Enclave-fähiger Schlüssel](always-encrypted-enclaves-rotate-keys.md)

## <a name="next-steps"></a>Nächste Schritte
- [Bereitstellen Enclave-fähiger Schlüssel](always-encrypted-enclaves-provision-keys.md)

## <a name="see-also"></a>Weitere Informationen  
- [Übersicht über die Schlüsselverwaltung für Always Encrypted](overview-of-key-management-for-always-encrypted.md)
- [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md)
