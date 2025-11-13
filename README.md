import statistics

# Lista de logs de treinamento: cada entrada é (epoch, tempo de execução em segundos)
training_logs = [
    (1, 3.91),
    (2, 3.95),
    (3, 4.11),
    (4, 3.88),
    (5, 4.03),
    (6, 4.05),
    (7, 3.99),
    (8, 4.02),
    (9, 3.96),
    (10, 3.98)
]

# Salva o log em arquivo
def save_log(logs, filename='train_log.txt'):
    with open(filename, 'w') as f:
        f.write("epoch,time_seconds\n")
        for epoch, t in logs:
            f.write(f"{epoch},{t}\n")
    print(f"Log salvo em: {filename}")

# Extrai só os tempos de execução
execution_times = [t for _, t in training_logs]

# Cálculo da média e desvio-padrão
mean_time = statistics.mean(execution_times)
stdev_time = statistics.stdev(execution_times)

print(f'Média do tempo de execução: {mean_time:.3f} segundos')
print(f'Desvio padrão do tempo de execução: {stdev_time:.3f} segundos')

# Salva o log
save_log(training_logs)
