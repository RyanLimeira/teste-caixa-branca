# teste-caixa-branca
# TESTE CAIXA BRANCA

## Código analisado:
```
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class User {
    public Connection conectarBD() {
        Connection conn = null;
        try{
            Class.forName(com.mysql.Driver.Manager).newInstance();
            String url = "jdbc:mysql://127.0.0.1/test?user=lopes&password=123";
            conn = DriverManager.getConnection(url);
        }catch (Exception e ) { }
        return conn;}
    public String nome="";
    public boolean result = false;
    public boolean verificarUsuario(String login, String senha){
       String sql = "";
       Connection conn = conectarBD();
       //INSTRUÇÃO SQL
       sql += "select nome from usuarios ";
       sql += "where login = " + " ' " + login + " ' ";
       sql += " and senha = " + " ' " + senha +  " ' ; ";
       try{
           Statement st = conn.createStatement();
           ResultSet rs = st.executeQuery(sql);
            if (rs.next()){
                result = true;
                nome = rs.getString("nome");}
            }catch (Exception e) { }
            return result;}
       }
```

## Pontos de observação

### A documentação foi descrita no código?
O código não contém nenhum tipo de documentação, nem mesmo possui comentários suficientes para o seu entendimento, o que seria uma boa prática.

### As variáveis e constantes possuem boa nomenclatura?
O código também não apresenta boas nomenclaturas, já que utiliza de variáveis com nome curtos e nada descritivos.

### Existem legibilidade e organização no código?
Não há formatação adequada, como por exemplo a identação, o que o torna difícil de ler.

### Todos os nullpointers foram tratados?
O código não trata adequadamente possíveis exceções de NullPointerException. Por exemplo, um NullPointerException poderia ser lançado caso 'conn' não seja inicializado corretamente.

### A arquitetura utilizada foi devidamente respeitada?
Não como se aprofundar neste tópico já que temos apenas um trecho do código, não o sistema completo.

### As conexões utilizadas foram fechadas?
Neste código não há chamadas para fechamento em nenhum momento, seja nas conexões, declarações ou resultados. É de extrema importância o fechamento para evitar vazamentos e para manter boas práticas de programação. 
