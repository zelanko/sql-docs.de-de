---
description: Beispiel zur Veranschaulichung der Verwendung von Always Encrypted mit Secure Enclaves mit einem Azure Key Vault-Anbieter
title: Beispiel zur Veranschaulichung der Verwendung von Always Encrypted mit Secure Enclaves mit einem Azure Key Vault-Anbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/17/2020
ms.reviewer: v-kaywon
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: karinazhou
ms.author: v-jizho2
ms.openlocfilehash: 39d03c4ddcf7edc7d0df1176c9aed1b92f9af9d5
ms.sourcegitcommit: 4c3949f620d09529658a2172d00bfe37aeb1a387
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2020
ms.locfileid: "96123974"
---
# <a name="example-demonstrating-use-of-azure-key-vault-provider-with-always-encrypted-enabled-with-secure-enclaves"></a>Beispiel zur Veranschaulichung der Verwendung von Always Encrypted mit Secure Enclaves mit einem Azure Key Vault-Anbieter

[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

[!INCLUDE [appliesto-netfx-netcore-xxxx-md](../../../includes/appliesto-netfx-netcore-netst-md.md)]

Dieses Beispiel veranschaulicht die Verwendung eines Azure Key Vault-Anbieters beim Zugriff auf verschlüsselte Spalten.

[!code-csharp [Azure Key Vault Provider with Enclave Example#1](~/../sqlclient/doc/samples/AzureKeyVaultProviderWithEnclaveProviderExample.cs#1)]

> [!NOTE]
> - Um Always Encrypted ohne sichere Enclaves für die Anwendung .NET Standard zu verwenden, ist mindestens Version 2.1.0 von **Microsoft.Data.SqlClient** erforderlich. Die unterstützte .NET Standard-Version ist 2.1 oder höher. 
>
> - Um Always Encrypted mit sicheren Enclaves unter Linux und macOS zu verwenden, ist mindestens Version 2.1.0 von **Microsoft.Data.SqlClient** erforderlich.

## <a name="see-also"></a>Weitere Informationen

- [Beispiel zur Veranschaulichung der Verwendung von Always Encrypted mit Secure Enclaves mit einem Azure Key Vault-Anbieter](azure-key-vault-example.md)
- [Tutorial: Entwickeln einer .NET-Anwendung mithilfe von Always Encrypted mit Secure Enclaves](tutorial-always-encrypted-enclaves-develop-net-apps.md)
- [Verwenden von Always Encrypted mit dem Microsoft .NET-Datenanbieter für SQL Server](sqlclient-support-always-encrypted.md)
