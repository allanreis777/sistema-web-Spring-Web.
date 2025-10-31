# sistema-web-Spring-Web.
att 3
package com.exemplo;

public class Produto {
    private Long id;
    private String nome;
    private String descricao;
    private Double preco;
    private Integer quantidade;

    // Getters e Setters
    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public String getDescricao() {
        return descricao;
    }

    public void setDescricao(String descricao) {
        this.descricao = descricao;
    }

    public Double getPreco() {
        return preco;
    }

    public void setPreco(Double preco) {
        this.preco = preco;
    }

    public Integer getQuantidade() {
        return quantidade;
    }

    public void setQuantidade(Integer quantidade) {
        this.quantidade = quantidade;
    }
}

package com.exemplo;

import java.util.ArrayList;
import java.util.List;

public class ProdutoService {
    private List<Produto> produtos = new ArrayList<>();
    private Long idCounter = 1L;

    public List<Produto> listarTodos() {
        return produtos;
    }

    public void salvar(Produto produto) {
        if (produto.getId() == null) {
            produto.setId(idCounter++);
            produtos.add(produto);
        } else {
            for (int i = 0; i < produtos.size(); i++) {
                if (produtos.get(i).getId().equals(produto.getId())) {
                    produtos.set(i, produto);
                    break;
                }
            }
        }
    }

    public Produto buscarPorId(Long id) {
        return produtos.stream().filter(p -> p.getId().equals(id)).findFirst().orElse(null);
    }

    public void deletar(Long id) {
        produtos.removeIf(p -> p.getId().equals(id));
    }
}
