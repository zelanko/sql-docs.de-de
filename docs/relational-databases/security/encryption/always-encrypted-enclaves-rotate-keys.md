---
title: Rotation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/31/2019
ms.prod: sql
ms.reviewer: vanto
ms.prod_service: database-engine, sql-database
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 5420d49b6e5d165168610d002424e3a3b9499748
ms.sourcegitcommit: 620a868e623134ad6ced6728ce9d03d7d0038fe0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87411056"
---
# <a name="rotate-enclave-enabled-keys"></a>Rotation von Enclave-fähigen Schlüsseln
[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

Bei Always Encrypted ist eine Schlüsselrotation ein Vorgang, bei dem ein vorhandener Spaltenhauptschlüssel oder ein Spaltenverschlüsselungsschlüssel durch einen neuen Schlüssel ersetzt wird. In diesem Artikel werden Anwendungsfälle und Überlegungen zur Schlüsselrotation bei [Always Encrypted mit Secure Enclaves](always-encrypted-enclaves.md) beschrieben, wenn der ursprüngliche Schlüssel und/oder der (neue) Zielschlüssel Enclave-fähig ist. Allgemeine Richtlinien und Verfahren zum Verwalten von Always Encrypted-Schlüsseln finden Sie unter [Übersicht über die Schlüsselverwaltung für Always Encrypted](overview-of-key-management-for-always-encrypted.md). 

Möglicherweise müssen Sie aus Sicherheits- oder Konformitätsgründen eine Schlüsselrotation durchführen. Dies kann beispielsweise der Fall sein, wenn ein Schlüssel kompromittiert wurde oder die Richtlinien Ihrer Organisation verlangen, dass Sie Schlüssel regelmäßig ersetzen. Zudem bietet die Schlüsselrotation mithilfe von Always Encrypted mit Secure Enclaves eine Möglichkeit, die Funktion der serverseitigen Secure Enclave für die verschlüsselten Spalten zu aktivieren oder zu deaktivieren.
- Wenn Sie einen nicht Enclave-fähigen Schlüssel durch einen Enclave-fähigen Schlüssel ersetzen, entsperren Sie die Funktion der Secure Enclave für Abfragen in einer mit dem Schlüssel geschützten Spalte. Weitere Informationen hierzu finden Sie unter [Aktivieren von Always Encrypted mit Secure Enclaves für vorhandene verschlüsselte Spalten](always-encrypted-enclaves-enable-for-encrypted-columns.md).
 - Wenn Sie einen Enclave-fähigen Schlüssel durch einen nicht Enclave-fähigen Schlüssel ersetzen, deaktivieren Sie die Funktion der Secure Enclave für Abfragen in einer mit diesem Schlüssel geschützten Spalte.

Wenn Sie eine Schlüsselrotation nur aus Sicherheits-/Konformitätsgründen durchführen und keine Enclave-Berechnungen für die Spalten aktivieren oder deaktivieren möchten, stellen Sie sicher, dass der Zielschlüssel in Bezug auf Enclaves dieselbe Konfiguration wie der Quellschlüssel aufweist. Wenn der Quellschlüssel beispielsweise Enclave-fähig ist, muss der Zielschlüssel ebenfalls Enclave-fähig sein.

Die folgenden allgemeinen Schritte enthalten je nach Rotationsszenario Links zu ausführlichen Artikeln:

1. Stellen Sie einen neuen Schlüssel (Spaltenhauptschlüssel oder Spaltenverschlüsselungsschlüssel) bereit.
    - Informationen zum Bereitstellen eines neuen Enclave-fähigen Schlüssel finden Sie unter [Bereitstellen Enclave-fähiger Schlüssel](always-encrypted-enclaves-provision-keys.md).
    - Informationen zum Bereitstellen eines nicht Enclave-fähigen Schlüssels finden Sie unter [Bereitstellen von Always Encrypted-Schlüsseln mithilfe von SQL Server Management Studio](configure-always-encrypted-keys-using-ssms.md) und unter [Bereitstellen von Always Encrypted-Schlüsseln mithilfe von PowerShell](configure-always-encrypted-keys-using-powershell.md).
2. Ersetzen Sie einen vorhandenen Schlüssel durch den neuen Schlüssel.
    - Wenn Sie eine Rotation mit einem Spaltenverschlüsselungsschlüssel durchführen und sowohl der Quellschlüssel als auch der Zielschlüssel Enclave-fähig ist, können Sie die Rotation (bei der die Daten erneut verschlüsselt werden) direkt ausführen. Informationen hierzu finden Sie unter [Konfigurieren einer direkten Spaltenverschlüsselung mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-configure-encryption.md).
    - Eine ausführliche Beschreibung der Schritte für die Schlüsselrotation finden Sie unter [Rotation von Always Encrypted-Schlüsseln mithilfe von SQL Server Management Studio](rotate-always-encrypted-keys-using-ssms.md) und unter [Rotation von Always Encrypted-Schlüsseln mithilfe von PowerShell](rotate-always-encrypted-keys-using-powershell.md).

    
## <a name="next-steps"></a>Nächste Schritte
- [Abfragen von Spalten mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-query-columns.md)
- [Konfigurieren einer direkten Spaltenverschlüsselung mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-configure-encryption.md)
- [Aktivieren von Always Encrypted mit Secure Enclaves für vorhandene verschlüsselte Spalten](always-encrypted-enclaves-enable-for-encrypted-columns.md)
- [Entwickeln von Anwendungen mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-client-development.md)  

## <a name="see-also"></a>Weitere Informationen  
- [Verwalten von Schlüsseln für Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-manage-keys.md)

