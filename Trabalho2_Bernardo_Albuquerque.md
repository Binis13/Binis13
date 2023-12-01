# Trabalho de Bases de Programação

Nome Aluno: Bernardo Albuquerque Ramos
Matrícula:1230119352
e-mail:bealbuquerqueramos@gmail.com

## Resposta 1
coordenadas geográficas, latitude e longitude e graus para radianos.

pseudocodigo aqui
algoritmo "Conversor de Coordenadas"

// Função para converter graus para radianos
funcao real grausParaRadianos(graus: real) : real
var
    radianos: real
inicio
    radianos <- graus * PI / 180
    retorne radianos
fim funcao

// Programa principal
var
    latitude, longitude, latitudeRadianos, longitudeRadianos: real

inicio

    escreva("Digite a latitude em graus: ")
    leia(latitude)
    
    escreva("Digite a longitude em graus: ")
    leia(longitude)
    
    // chamar função converter graus para radianos
    latitudeRadianos <- grausParaRadianos(latitude)
    longitudeRadianos <- grausParaRadianos(longitude)

    // Mostrar resultados
    escreva("Latitude em radianos: ", latitudeRadianos)
    escreva("Longitude em radianos: ", longitudeRadianos)
    
fim

## Resposta 2
Calculando a distância de duas posições com latitude e longitude usando a formula de Harvesine.

pseudocodigo aqui

funcao graus_para_radianos(graus: real) : real
inicio
    retorne graus * PI / 180.0
fim

funcao distancia_haversine(lat1, lon1, lat2, lon2: real) : real
inicio
    // Raio da Terra em quilômetros
    const RAIO_TERRA = 6371.0
    
    // Converte graus para radianos
    lat1 = graus_para_radianos(lat1)
    lon1 = graus_para_radianos(lon1)
    lat2 = graus_para_radianos(lat2)
    lon2 = graus_para_radianos(lon2)
    
    // Diferença das latitudes e longitudes
    delta_lat = lat2 - lat1
    delta_lon = lon2 - lon1
    
    // Fórmula de Haversine
    a = seno(delta_lat / 2) * seno(delta_lat / 2) +
        cos(lat1) * cos(lat2) *
        seno(delta_lon / 2) * seno(delta_lon / 2)
    
    c = 2 * atan2(raiz(a), raiz(1 - a))
    
    // Distância em quilômetros
    distancia = RAIO_TERRA * c
    
    retorne distancia
fim

// Exemplo de uso
lat1 = -23.550520
lon1 = -46.633308
lat2 = -22.9035
lon2 = -43.2096

distancia_entre_pontos = distancia_haversine(lat1, lon1, lat2, lon2)

escreva("A distância entre os pontos é: ", distancia_entre_pontos, " km")

## Resposta 3
calculando a antípoda de uma localidade informada com latitude e longitude.

pseudocodigo aqui
funcao graus_para_radianos(graus: real) : real
inicio
    retorne graus * PI / 180.0
fim

funcao distancia_haversine(lat1, lon1, lat2, lon2: real) : real
inicio
    // Implementação da função de Haversine (como mencionado anteriormente)
    // ...

// Função para calcular a antípoda
funcao calcular_antipoda(lat, lon: real) : registro
inicio
    const LATITUDE_MAXIMA = 90.0
    const LONGITUDE_MAXIMA = 180.0
    
    // Calcula a latitude da antípoda
    antipoda_lat = -lat
    
    // Calcula a longitude da antípoda, considerando o hemisfério oposto
    antipoda_lon = lon + 180.0
    se antipoda_lon > LONGITUDE_MAXIMA entao
        antipoda_lon = antipoda_lon - 360.0
    fimse
    
    // Retorna a antípoda como um registro
    retorne registro(lat: antipoda_lat, lon: antipoda_lon)
fim

// Programa principal
inicio
    // Recebe as coordenadas da localidade original
    escreva("Informe a latitude da localidade original: ")
    leia(lat_original)
    escreva("Informe a longitude da localidade original: ")
    leia(lon_original)

    // Calcula a antípoda
    antipoda = calcular_antipoda(lat_original, lon_original)
    
    // Imprime as coordenadas da antípoda
    escreva("As coordenadas da antípoda são: (", antipoda.lat, ", ", antipoda.lon, ")\n")
    
    // Calcula a distância entre a localidade original e a antípoda
    distancia_entre_pontos = distancia_haversine(lat_original, lon_original, antipoda.lat, antipoda.lon)
    
    // Imprime a distância
    escreva("A distância entre a localidade original e sua antípoda é: ", distancia_entre_pontos, " km\n")
fim
