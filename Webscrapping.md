## Projeto para extrair os destaques de notícias do veículo de mídia BBC
* Utilizando o **BeutifulSoup** pude aplicar a técnica de **webscrapping** para extrair informações das headlines do dia.
* Tendo as informações tratadas, utilizei o **WorldCloud** para extrair e plotar em palavras-chave o destaques atualizados.
* Com isso podemos ter acesso a informações de forma veloz toda vez que rodarmos o script.  


```python
import requests
import pandas as pd
from bs4 import BeautifulSoup
```


```python
url = 'https://www.bbc.com/'
page = requests.get(url)
soup = BeautifulSoup(page.text, 'html')
```


```python
headline = soup.find_all('h2')  #após inpecionar o portal, a tag <h2> é a que desejamos para coletar as headlines 
text = ''
for i in headline: #utilizando um laço para extrair e concatenar todas as headlines
    text+=" "+i.text+" "
```


```python
print(text) #verificando o conteúdo das headlines que foi extraído e concatenado
```

     In maps: The war-ravaged Ukrainian territories at the heart of the Trump-Putin summit  Wildfire menaces major Greek city as heatwave grips Europe  In maps: The war-ravaged Ukrainian territories at the heart of the Trump-Putin summit  Wildfire menaces major Greek city as heatwave grips Europe  European leaders tentatively hopeful after call with Trump ahead of Putin summit  'Our children are dying' - rare footage shows plight of civilians in besieged Sudan city  Timelapse captures rising glacial lakes in Alaska  Sylvester Stallone among Kennedy Center honourees announced by Trump  Air Canada to begin cancelling flights ahead of potential strike  Only from the BBC  When Indian professor's viral chemistry defence failed in husband's murder trial  The radical manifesto hidden in a masterpiece   UEFA Super Cup  Super Cup: PSG beat Spurs on penalties after coming from 2-0 down - report & highlights  Global News Podcast  More news  The row over 'vote theft' that has shaken Indian politics  Gaza talks to focus on releasing hostages all in one go, Netanyahu hints  'Cryptocrash king' Do Kwon pleads guilty to fraud  Man charged with murder of Australian couple in graffiti-covered house  London chess prodigy, 10, becomes master player  Gaza talks to focus on releasing hostages all in one go, Netanyahu hints  South Korea's former first lady arrested for corruption  UK firms chase £38bn India contracts but challenges loom  'Cryptocrash king' Do Kwon pleads guilty to fraud  Must watch  Watch: Wildfire approaches horse enclosure in Greece  Aerial footage shows aftermath of massive train derailment in Texas  The hybrid human-Neanderthal fossils that shocked scientists  Europe's wildfires seen from above  Crime in DC: What do the figures say?  Clouds of smoke fill the skies as Canada wildfires rage  Video shows wallaby running in English countryside  Dramatic lightning strike causes tower of flames next to motorway  Technology  How language is hiding the real internet from you  Travel  The ethics of traveling to a vanishing destination  US & Canada news  Family of three killed during Tennessee floods  Evacuations in Alaska after glacial melt raises fears of record flooding  National Guard troops appear in Washington DC as mayor rejects Trump's 'authoritarian push'  US says UK human rights have worsened in past year  More world news  Jimmy Lai: Landmark trial of Hong Kong's rebel mogul resumes  Peru president issues amnesty for hundreds accused of atrocities  Trial of Labour MP Tulip Siddiq begins in Bangladesh  Cape Verde declares state of emergency after deadly floods  Sport  No plans for Premier League match abroad - Masters  'High stakes game of poker' - Newcastle 'together' despite Isak saga  Liverpool closing in on deal for Parma teenager Leoni  Warner's Ashes jibe 'part of the fun' - Root  Business   Inside Australia's billion-dollar bid to take on China's rare earth dominance  Claire's falls into administration with 2,150 jobs at risk  Bezos-backed Perplexity AI makes surprise bid for Google Chrome  Apple rejects Musk's App Store bias claims   Latest audio  World Business Report  World Business Report  Football Daily  Football Daily  Witness History  Global News Podcast  The Documentary Podcast  The Interview  Tech  FM26 drops first look after months of silence  Porn site traffic plummets as UK age verification rules enforced  'One video about a dress made me £6,000'  England expands police use of facial recognition vans  Science & health  Survival rates for most deadly cancers making little progress, experts warn  Seles reveals myasthenia gravis diagnosis  Should we all be taking vitamin supplements?  Cats develop dementia in a similar way to humans  Culture  BBC apologises after Jenrick accused of xenophobia  Teens arrested for Brad Pitt burglary targeted other stars, say LA police  'We had too much drama': Meet the Real Housewives of London  UFC to host first-ever fight event at the White House  Arts   Miriam Margolyes: 'We'll all die, but I'm not going yet'  The curious story of Britain's most famous WW2 poster  Why the Statue of Liberty is at the heart of a culture war  Fake or Fortune finds £35 painting is worth £50,000  Watch  Watch Spinosaurus' fierce fight for food and survival  Travel  Argentina's wild new coastal escape  The US town built by and for Chinese people  The end of 'perfect timing' for travellers  Is hitchhiking making a comeback?  World's Table  Costa Rica's nine-course meal in the sky  What is 'real' Italian pizza?  The 'other' Michelin award travellers should know  Eight cooling foods to beat the heat in Japan  Earth  Greece battles wildfires as heatwave rages across southern Europe  Worst bleaching on record for Western Australian coral reefs  Man faces jail in US for shipping 850 turtles in socks to Hong Kong  Flames near Madrid as wildfires burn across Spain and Portugal  Video  Watch kitten try to catch fish for the first time  Behind the scenes at Gaudi's stunning La Sagrada Familia  Do you need to drink electrolytes to stay hydrated?  What happened at Hiroshima?  Discover more from the BBC  In History  Download the BBC app  Health Fix  Register for a BBC account  Sign up for the Essential List  Sign up to News Briefing 
    


```python
# Importando as bibliotecas para nuvem de palavras
from wordcloud import WordCloud
import matplotlib.pyplot as plt

# Criando um objeto a partir do texto concatenado que foi retirado do veículo BBC
wordcloud = WordCloud(width=800, height=400, background_color='white').generate(text)

# Preparando a plotagem
plt.figure(figsize=(10, 5))
plt.imshow(wordcloud)
# Escondendo os eixos
plt.axis('off')
plt.tight_layout(pad=0)
plt.show()
```


    
![png](output_5_0.png)
    

