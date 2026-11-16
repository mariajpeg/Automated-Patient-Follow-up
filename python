# Valida os dados do formulário e calcula o próximo dia útil.


def ano_bissexto(ano):
    # Bissexto: divisível por 400, ou divisível por 4 mas não por 100
    if ano % 400 == 0:
        return True
    if ano % 100 == 0:
        return False
    return ano % 4 == 0


def dias_no_mes(mes, ano):
    if mes == 2:
        if ano_bissexto(ano):
            return 29
        return 28
    if mes in [4, 6, 9, 11]:
        return 30
    return 31


def separar_data(texto):
    # Aceita DD/MM/AAAA ou AAAA-MM-DD (formato do campo de data do formulário)
    if "/" in texto:
        partes = texto.split("/")
        if len(partes) != 3:
            raise ValueError("Data inválida. Use DD/MM/AAAA.")
        dia, mes, ano = partes
    elif "-" in texto:
        partes = texto[:10].split("-")
        if len(partes) != 3:
            raise ValueError("Data inválida. Use DD/MM/AAAA.")
        ano, mes, dia = partes
    else:
        raise ValueError("Data inválida. Use DD/MM/AAAA.")

    if not (dia.isdigit() and mes.isdigit() and ano.isdigit()):
        raise ValueError("Data inválida. Use DD/MM/AAAA.")

    dia = int(dia)
    mes = int(mes)
    ano = int(ano)

    if mes < 1 or mes > 12:
        raise ValueError("Mês inválido na data informada.")
    if dia < 1 or dia > dias_no_mes(mes, ano):
        raise ValueError("Essa data não existe no calendário.")
    return dia, mes, ano


def dia_da_semana(dia, mes, ano):
    # Fórmula de Zeller. Resultado: 0=sábado, 1=domingo, 2=segunda, ... 6=sexta
    if mes < 3:
        mes = mes + 12
        ano = ano - 1
    k = ano % 100
    j = ano // 100
    return (dia + (13 * (mes + 1)) // 5 + k + k // 4 + j // 4 + 5 * j) % 7


def somar_um_dia(dia, mes, ano):
    dia = dia + 1
    if dia > dias_no_mes(mes, ano):
        dia = 1
        mes = mes + 1
    if mes > 12:
        mes = 1
        ano = ano + 1
    return dia, mes, ano


def proximo_dia_util(dia, mes, ano):
    semana = dia_da_semana(dia, mes, ano)
    dia, mes, ano = somar_um_dia(dia, mes, ano)
    semana = (semana + 1) % 7
    # Enquanto cair em sábado (0) ou domingo (1), anda mais um dia
    while semana == 0 or semana == 1:
        dia, mes, ano = somar_um_dia(dia, mes, ano)
        semana = (semana + 1) % 7
    return dia, mes, ano


def formatar(dia, mes, ano):
    return f"{dia:02d}/{mes:02d}/{ano}"


resultado = []

for item in _items:
    dados = item["json"]
    nome = str(dados.get("Nome do paciente") or "").strip()
    data_texto = str(dados.get("Data do atendimento") or "").strip()
    observacoes = str(dados.get("Observações") or "").strip()

    if nome == "":
        raise ValueError("O nome do paciente é obrigatório.")
    if data_texto == "":
        raise ValueError("A data do atendimento é obrigatória.")

    dia, mes, ano = separar_data(data_texto)
    dia_f, mes_f, ano_f = proximo_dia_util(dia, mes, ano)

    resultado.append({
        "json": {
            "nome_paciente": nome,
            "data_atendimento": formatar(dia, mes, ano),
            "data_acompanhamento": formatar(dia_f, mes_f, ano_f),
            "observacoes": observacoes,
            "status": "Pendente",
            # Wait: 08:00 (Brasília) do dia do acompanhamento
            "data_hora_lembrete": f"{ano_f:04d}-{mes_f:02d}-{dia_f:02d}T08:00:00-03:00",
        }
    })

return resultado
