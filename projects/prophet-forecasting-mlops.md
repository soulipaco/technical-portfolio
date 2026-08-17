# Prophet Forecasting MLOps

[Repository](https://github.com/soulipaco/prophet-forecasting-mlops) · [Architecture](https://github.com/soulipaco/prophet-forecasting-mlops/blob/main/docs/architecture.md) · [Claims traceability](https://github.com/soulipaco/prophet-forecasting-mlops/blob/main/docs/claims_traceability.md)

## The problem

Forecasting notebooks often demonstrate a model but leave collection orchestration, time-aware evaluation, run identity, failure behavior, stable outputs, and deployment boundaries implicit.

## What was built

This project packages daily preparation, holiday/regressor construction, adaptive Prophet cross-validation, Optuna search, evaluation, final fitting, and collection orchestration in regular Python. Databricks-specific code handles Spark/Delta input and output, MLflow lineage, and Asset Bundle delivery.

Each collection run records forecasts, backtests, selected parameters, per-fit status, and a run manifest. A deterministic synthetic source provides two series and two targets without relying on private data.

## Decisions worth inspecting

- Time-aware split geometry adapts to the available history.
- The collection is the tracking unit rather than one registered model per fit.
- Repeated logical run IDs replace their earlier records before append.
- Stable batch tables are the interface; the project does not add unsupported online serving.
- The README explicitly lists operational capabilities that are not implemented.

## Evidence

The checked-in synthetic run records four completed fits, no failed fits, 832 forecast rows, 84 backtest rows, and ten passing local tests. The CI workflow also checks lint and formatting. These results validate execution and output contracts; they do not establish production forecast accuracy.

![Synthetic forecast generated from the packaged pipeline](../assets/projects/prophet-forecast.png)

## Best next clicks

- [Local validation commands](https://github.com/soulipaco/prophet-forecasting-mlops#local-validation)
- [Output contracts](https://github.com/soulipaco/prophet-forecasting-mlops#output-contracts)
- [Validation report](https://github.com/soulipaco/prophet-forecasting-mlops/blob/main/docs/validation_report.md)
- [Synthetic forecast data](https://github.com/soulipaco/prophet-forecasting-mlops/blob/main/assets/portfolio/synthetic_forecast.csv)

[Back to portfolio](../README.md)
