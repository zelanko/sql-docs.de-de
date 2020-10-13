---
title: Installieren von „azdata“ für macOS
titleSuffix: ''
description: Hier erfahren Sie, wie Sie das Tool „azdata“ unter macOS installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 19a3542f77708dcf779cf01d5299e7ff6add8273
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725241"
---
# <a name="install-azdata-on-macos"></a>Installieren von `azdata` unter macOS

Bei Verwendung der macOS-Plattform können Sie die `azdata-cli` mit dem Homebrew-Paket-Manager installieren. Das CLI-Paket wurde unter folgenden macOS-Versionen getestet:

- 10.13 High Sierra
- 10.14 Mojave
- 10.15 Catalina

## <a name="install-with-homebrew"></a>Installieren mit Homebrew

```bash
brew tap microsoft/azdata-cli-release
brew update
brew install azdata-cli
```

>[!IMPORTANT]
>Die `azdata-cli` weist eine Abhängigkeit von den Homebrew-Paketen `python3`, `freetds`, `unixodbc` und `zeromq` auf und installiert diese. Die `azdata-cli` ist garantiert kompatibel mit der aktuellen Version dieser Abhängigkeiten, die in Homebrew veröffentlicht wurde.

## <a name="verify-install"></a>Überprüfen der Installation

```bash
azdata
azdata --version
```

## <a name="update"></a>Aktualisieren

Aktualisieren Sie Ihre lokalen Repositoryinformationen, und upgraden Sie anschließend das Paket `azdata-cli`.

```bash
brew tap microsoft/azdata-cli-release
brew update
brew upgrade azdata-cli
```

## <a name="uninstall"></a>Deinstallieren

Verwenden Sie Homebrew, um das Paket `azdata-cli` zu deinstallieren.

```bash
brew uninstall azdata-cli
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).

Verwenden von azdata mit [Azure Arc-fähigen Datendiensten](/azure/azure-arc/data/)
