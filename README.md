import tkinter as tk
from tkinter import messagebox

# Funções dos caminhos
def caminho_das_sombras():
    resposta = simple_input("Enigma", 
        "Você escolheu o Caminho das Sombras.\n\n"
        "Este caminho é cercado por árvores antigas e sombrias.\n"
        "Você encontra uma criatura mágica guardiã do caminho.\n\n"
        "O enigma é:\n'Quem sou eu? Tenho olhos, mas não vejo. Tenho boca, mas não falo. O que sou?'\n\n"
        "Digite sua resposta:")
    
    if resposta and resposta.lower() == "caveira":
        messagebox.showinfo("Resultado", "Resposta correta! Você encontrou um baú escondido contendo uma gema preciosa que vale 100 pontos.")
    else:
        messagebox.showwarning("Resultado", "Resposta incorreta. Você não conseguiu passar pelo Caminho das Sombras.")


def caminho_da_luz():
    opcao = simple_input("Caminho da Luz", 
        "Você escolheu o Caminho da Luz.\n\n"
        "Este caminho é iluminado por raios de sol.\n"
        "Você encontra uma ponte quebrada sobre um rio turbulento.\n\n"
        "Digite 'atravessar' para tentar atravessar a ponte ou 'desvio' para procurar um desvio seguro:")
    
    if opcao and opcao.lower() == "atravessar":
        messagebox.showinfo("Resultado", "Você conseguiu atravessar, mas a ponte quase desabou! Avançou para a próxima etapa.")
    elif opcao and opcao.lower() == "desvio":
        messagebox.showinfo("Resultado", "Você encontrou um desvio seguro, mas demorou muito e perdeu parte de sua energia.")
    else:
        messagebox.showwarning("Resultado", "Opção inválida!")


def caminho_das_criaturas():
    opcao = simple_input("Caminho das Criaturas", 
        "Você escolheu o Caminho das Criaturas.\n\n"
        "Um grupo de criaturas bloqueia sua passagem.\n\n"
        "Digite 'lutar' para enfrentar as criaturas ou 'enganar' para tentar enganá-las:")
    
    if opcao and opcao.lower() == "lutar":
        messagebox.showinfo("Resultado", "Você lutou bravamente e derrotou as criaturas, mas saiu ferido da batalha.")
    elif opcao and opcao.lower() == "enganar":
        messagebox.showinfo("Resultado", "Você conseguiu enganar as criaturas com inteligência e passou sem lutar.")
    else:
        messagebox.showwarning("Resultado", "Opção inválida!")


# Função auxiliar para pegar entrada do usuário em caixa de diálogo
def simple_input(title, prompt):
    input_win = tk.Toplevel(root)
    input_win.title(title)
    input_win.geometry("400x250")
    tk.Label(input_win, text=prompt, wraplength=380, justify="left").pack(pady=10)
    
    entry = tk.Entry(input_win, width=30)
    entry.pack(pady=5)

    resposta = {"value": None}
    
    def confirmar():
        resposta["value"] = entry.get()
        input_win.destroy()

    tk.Button(input_win, text="Confirmar", command=confirmar).pack(pady=10)
    
    input_win.transient(root)
    input_win.grab_set()
    root.wait_window(input_win)
    return resposta["value"]


# Interface principal
root = tk.Tk()
root.title("Aventura na Floresta")
root.geometry("500x300")

label = tk.Label(root, text="Você é um explorador que se aventura em uma misteriosa floresta\n"
                            "em busca de tesouro lendário e segredos perdidos.\n\n"
                            "Ao adentrar na floresta, você se depara com três caminhos.\n"
                            "Escolha um deles:", justify="center", wraplength=480)
label.pack(pady=20)

btn1 = tk.Button(root, text="1 - Caminho das Sombras", width=30, command=caminho_das_sombras)
btn1.pack(pady=5)

btn2 = tk.Button(root, text="2 - Caminho da Luz", width=30, command=caminho_da_luz)
btn2.pack(pady=5)

btn3 = tk.Button(root, text="3 - Caminho das Criaturas", width=30, command=caminho_das_criaturas)
btn3.pack(pady=5)

root.mainloop()
