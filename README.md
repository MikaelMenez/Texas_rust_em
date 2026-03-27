
---

# Texas Rust'em 🃁 

**Texas Rust'em** é uma biblioteca leve e idiomática em Rust para gerenciamento de cartas, baralhos e jogadores, projetada especificamente para lógica de poker Texas Hold'em.

A biblioteca utiliza caracteres Unicode reais para renderizar as cartas no terminal, proporcionando uma experiência visual rica durante o desenvolvimento e execução de jogos CLI.

## ✨ Funcionalidades

* **Representação Visual:** Cartas renderizadas com símbolos Unicode (ex: 🂡, 🂮).
* **Gerenciamento de Baralho:** Criação de baralho padrão de 52 cartas, embaralhamento e remoção segura (pop).
* **Entidades de Poker:** Tipos integrados para `Player`, `Blinder` (Dealer, Small Blind, Big Blind) e `Card`.
* **Ordenação:** Implementação de `Ord` e `PartialOrd` para comparação direta de força entre cartas.

## 🚀 Instalação

Adicione ao seu `Cargo.toml`:

```toml
[dependencies]
texas_rust_em = "0.1.0"
rand = "0.9" # Necessário para embaralhar
```

## 🛠️ Como usar

Aqui está um exemplo rápido de como criar um baralho, embaralhá-lo e distribuir cartas para um jogador:

```rust
use texas_rust_em::texas_rust_em::{Card, Deck, Player, Blinder};

fn main() -> Result<(), texas_rust_em::texas_rust_em::DeckError> {
    // 1. Criar e inicializar um baralho padrão
    let mut baralho = Card::deck();
    
    // 2. Embaralhar
    Card::suffle(&mut baralho);
    
    // 3. Criar um jogador (ex: Dealer)
    let mut jogador = Player::new(Blinder::Dealer);
    
    // 4. Distribuir a mão (2 cartas)
    jogador.get_hand(&mut baralho)?;
    
    // 5. Exibir resultados
    println!("Baralho restante: {}", baralho);
    println!("Jogador: {}", jogador);

    Ok(())
}
```

## 🎴 Representação de Cartas

A biblioteca mapeia as cartas para o bloco de símbolos de cartas do Unicode (`U+1F0A0` a `U+1F0DF`). Ao imprimir uma carta ou o baralho, você verá os símbolos reais, facilitando o debug visual.

## ⚖️ Licença

Distribuído sob as licenças MIT ou Apache-2.0. Veja os arquivos `LICENSE-MIT` e `LICENSE-APACHE` para mais detalhes.

---

### Dicas para o seu `Cargo.toml` antes de publicar:

Como seu código usa a crate `rand`, certifique-se de que as dependências estão assim no arquivo oficial:

```toml
[package]
name = "texas_rust_em"
version = "0.1.0"
edition = "2021"
description = "A Texas Hold'em poker engine with Unicode card support"
license = "MIT OR Apache-2.0"
repository = "https://github.com/seu-usuario/texas_rust_em"
keywords = ["poker", "cards", "game", "texas-holdem"]
categories = ["games"]

[dependencies]
rand = "0.9" # Ou a versão que você configurou
```

**Gostaria que eu fizesse alguma alteração específica na descrição ou nos exemplos?**
