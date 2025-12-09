# m2-unity
## opdracht 1.2 herhaling
#### 1A
![Unity](/img/Schermafbeelding%202025-11-18%20123553.png)
## SCRIPT:

public class RandomItem : MonoBehaviour
{
    [SerializeField]
    private string[] itemNames = new string[10];

    void Update()
    {
      
        if (Input.GetKeyDown(KeyCode.Return))
        {
            PrintRandomItem();
        }

       
        if (Input.GetKeyDown(KeyCode.Escape))
        {
            PrintAllItems();
        }
    }

    private void PrintRandomItem()
    {
        
        int randomIndex = Random.Range(0, itemNames.Length);
        Debug.Log("Willekeurig item: " + itemNames[randomIndex]);
    }

    private void PrintAllItems()
    {
        Debug.Log("Alle items:");
        for (int i = 0; i < itemNames.Length; i++)
        {
            Debug.Log("Item " + i + ": " + itemNames[i]);
        }
    }
}



## Opdracht 1.1 concept
Titel: Parry peggle
Genre: Action, Physics-based arcade puzzelgame.

Beschrijving: De speler is een ninja die uit een canon word geschoten met een zwaard die het doel heeft om beneden te komen door de balletjes weg te slaan voor punten. Als de speler valt zijn er enemies met pistolen die hij moet deflecten om het te halen, anders pak je damage tot dat je levens op is.

Gameplaykern
Bal: Een ninja (getekent als een bal) met een zwaard
Targets of bumps: Zwarte balletjes die punten zijn als je ze slashed
Score: 1 bal is gewoon 1 gold, maar sommige kunnen groter zijn waardoor je 5-10 gold kan krijgen. 
Doel: Je moet zoveel mogelijk gold pakken anders haal je de level niet, bijvoorbeeld je hebt 10 gold nodig om door de hol te gaan voor de volgende level
Stijl en sfeer: Pixelated stijl vecht sfeer
Korte omschrijving van thema, kleuren en geluid: de thema is gewoon om ninjas. de kleuren zijn een beetje donker en het geluid is gewoon calm.

Structuur van het level
Bovenaan: de kanon waar je kan kiezen waar je de speler eruit wilt schieten
Midden: veld met balletjes waar je ze moet aanvallen, en de enemies die je probeert te schieten waar je de kogels moet parryen

Onderaan: opvang of doelgebied waar je gold nodig hebt om naar de volgende level te gaan


<img width="623" height="854" alt="image" src="https://github.com/user-attachments/assets/f2c2e65f-5d3e-4667-9aea-fa449f804775" />


## Opdracht 2.1 Forces and Collision

Hier hit de bal de target wat er werd gevraagd in de opdracht:



https://github.com/user-attachments/assets/7710b05e-d5fd-4d5f-8b46-eb72f0beb951

