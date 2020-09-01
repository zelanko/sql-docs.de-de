---
title: Importieren oder Anzeigen von Modellen mit der Machine Learning-Erweiterung
titleSuffix: Azure Data Studio
description: Hier erfahren Sie, wie Sie die Machine Learning-Erweiterung für Azure Data Studio verwenden, um ein ONNX-Modell zu importieren oder bereits importierte Modelle in der Datenbank anzuzeigen.
ms.date: 06/09/2020
ms.reviewer: sstein
ms.prod: azure-data-studio
ms.technology: machine-learning
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 3c5faa821ecd9adcfcea426f88a388a6f7d10f27
ms.sourcegitcommit: 6d53ecfdc463914f045c20eda96da39dec22acca
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88901052"
---
# <a name="import-or-view-models-with-machine-learning-extension-preview-for-azure-data-studio"></a>Importieren oder Anzeigen von Modellen mit der Machine Learning-Erweiterung (Vorschauversion) für Azure Data Studio

Hier erfahren Sie, wie Sie die [Machine Learning-Erweiterung für Azure Data Studio](machine-learning-extension.md) verwenden, um ein ONNX-Modell zu importieren oder bereits importierte Modelle in der Datenbank anzuzeigen.

> [!IMPORTANT]
> Der Import und die Ansicht in einer Datenbank mit der Machine Learning-Erweiterung unterstützen derzeit nur [Machine Learning Services in Azure SQL Managed Instance](/azure/azure-sql/managed-instance/machine-learning-services-overview) und [Azure SQL Edge mit ONNX](/azure/azure-sql-edge/onnx-overview).

## <a name="prerequisites"></a>Voraussetzungen

- Installieren und konfigurieren Sie die [Machine Learning-Erweiterung für Azure Data Studio](machine-learning-extension.md). Sie müssen die [Python-Installationspfade in den Erweiterungseinstellungen](machine-learning-extension.md#settings) angeben.

- Sie benötigen die Python-Pakete **onnxruntime**, **mlflow** und **mlflow-dbstore**. Wenn die Pakete nicht bereits installiert sind, werden Sie von der Machine Learning-Erweiterung dazu aufgefordert, diese zu installieren.

## <a name="view-models"></a>Modelle anzeigen

Führen Sie die folgenden Schritte durch, um die in Ihrer Datenbank gespeicherten ONNX-Modelle anzuzeigen.

1. Klicken Sie auf **Import or view models** (Modelle importieren oder anzeigen).

1. Wenn Sie zur Installation von **onnxruntime**, **mlflow** und **mlflow-dbstore** aufgefordert werden, klicken Sie auf **Ja**.

1. Wählen Sie die **Modelldatenbank** und die **Modelltabelle** aus, in der die Modelle gespeichert werden.

Dadurch wird eine Liste Ihrer Modelle angezeigt. Sie können den Modellnamen und die Beschreibung bearbeiten oder ein Modell aus der Liste löschen.

## <a name="import-a-new-model"></a>Importieren eines neuen Modells

Führen Sie die folgenden Schritte durch, um ein ONNX-Modell in Ihre Datenbank zu importieren.

1. Klicken Sie auf **Import or view models** (Modelle importieren oder anzeigen).

1. Wenn Sie zur Installation von **onnxruntime**, **mlflow** und **mlflow-dbstore** aufgefordert werden, klicken Sie auf **Ja**.

1. Klicken Sie auf **Import models** (Modelle importieren).

1. Wählen Sie die **Modelldatenbank** aus, in der Sie das importierte Modell speichern möchten.

1. Wählen Sie die **Modelltabelle** aus, in der Sie das importierte Modell speichern möchten. Sie können entweder eine **vorhandene Tabelle** auswählen oder eine **neue Tabelle** erstellen. Klicken Sie auf **Weiter**.

1. Wählen Sie den Speicherort des Modells aus, und klicken Sie auf **Weiter**. Verwenden Sie Folgendes:
    - **Dateiupload:** Wählen Sie diese Option aus, um ein Modell aus einer Datei zu verwenden. Wählen Sie die Modelldatei unter **Quelldateien** aus, und klicken Sie auf **Weiter**.
    - **Azure Machine Learning:** Wählen Sie diese Option aus, um ein Modell aus Azure Machine Learning zu verwenden. Zunächst müssen Sie sich **bei Azure anmelden**. Wählen Sie dann Ihr **Azure-Konto**, Ihr **Azure-Abonnement**, Ihre **Azure-Ressourcengruppe** und Ihren **Azure ML-Arbeitsbereich** aus. Wählen Sie das gewünschte Modell aus, und klicken Sie auf **Weiter**.

1. Geben Sie **Name** und **Beschreibung** des Modells ein, und klicken Sie auf **Bereitstellen**, um das Modell in Ihrer Datenbank zu speichern.

> [!NOTE]
> Die Machine Learning-Erweiterung befindet sich derzeit in der Vorschauphase. Daher kann sich das Tabellenschema, in dem die Modelle gespeichert werden, in Zukunft ändern.

## <a name="next-steps"></a>Nächste Schritte

- [Machine Learning-Erweiterung in Azure Data Studio](machine-learning-extension.md)
- [Verwalten von Paketen in der Datenbank](machine-learning-extension-manage-packages.md)
- [Treffen von Vorhersagen](machine-learning-extension-predictions.md)
- [SQL Machine Learning-Dokumentation](../machine-learning/index.yml)
- [Machine Learning Services in Azure SQL Managed Instance (Vorschauversion)](/azure/azure-sql/managed-instance/machine-learning-services-overview)
- [Machine Learning und KI mit ONNX in SQL Edge (Vorschau)](/azure/azure-sql-edge/onnx-overview)
