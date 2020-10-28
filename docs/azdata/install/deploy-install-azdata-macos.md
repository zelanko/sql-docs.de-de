---
title: Installieren der Azure Data CLI (azdata) für macOS
titleSuffix: ''
description: Erfahren Sie, wie Sie das Tool Azure Data CLI (azdata) unter macOS installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0e3d7217ef917c794f1c497f7c5548588c2da1ba
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257380"
---
# <a name="install-azure-data-cli-azdata-on-macos"></a>Installieren von [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)] unter macOS

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
