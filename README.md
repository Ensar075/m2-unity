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

dit is de bal code:
using UnityEngine;

public class ShootBall : MonoBehaviour
{


    
    public float ShootForce = 500f;

   
    public Vector3 Direction = new Vector3(0f, 1f, 0f);

    private Rigidbody2D rb;

   
    void Start()
    {
       
        rb = GetComponent<Rigidbody2D>();
    }

    
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.A))
        {
         
            rb.AddForce(Direction * ShootForce);

        }
    }


dit is de target code:

using UnityEngine;

public class TargetCollision : MonoBehaviour
{
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
     
    
    }
    void OnCollisionEnter2D(Collision2D collision)
    {
        Debug.Log("Hit!");
    }


## Opdracht 2.2: Mikken, Shieten en Line Renderer
Dit is de video van de opdracht


https://github.com/user-attachments/assets/60a5fcb7-ee2e-451b-a07e-c9885303c711

scripts:
aim.cs:
using UnityEngine;
public class Aim : MonoBehaviour
{
    void Update()
    {
       
        Vector3 pos = Camera.main.WorldToScreenPoint(transform.position);
       
        Vector3 dir = Input.mousePosition - pos;
        
        float angle = Mathf.Atan2(dir.y, dir.x) * Mathf.Rad2Deg;
       
        transform.rotation = Quaternion.AngleAxis(angle, Vector3.forward);
    }
}
schoot.cs:
using UnityEngine;

public class Shoot : MonoBehaviour
{
    private void Start()
    {
        
        _line = GetComponent<LineRenderer>();
       
        _line.SetPosition(1, Vector3.zero);
       

    }
    
    [SerializeField] private float lineSpeed = 10f;
   
    private LineRenderer _line;
    
    private bool _lineActive = false;
  
  
    [SerializeField] private GameObject prefab;
    
    [SerializeField] private float forceBuild = 20f;

    [SerializeField] private float maximumHoldTime = 5f;

   

   
    private float _pressTimer = 0f;
   
    private float _launchForce = 0f;

    
    private void Update()
    {
        HandleShot();
        if (Input.GetMouseButtonDown(0))
        {
            _pressTimer = 0f;
            _lineActive = true;
        }
        if (Input.GetMouseButtonUp(0))
        {

            


            _lineActive = false;
            _line.SetPosition(1, Vector3.zero);
        }
    }
    
    private void HandleShot()

    {
        if (_lineActive)
        {
            _line.SetPosition(1, Vector3.right * _pressTimer * lineSpeed);
        }
       
        if (Input.GetMouseButtonDown(0))
        {
            _pressTimer = 0; 

        }
        
        if (Input.GetMouseButtonUp(0))
        {
          
            _launchForce = _pressTimer * forceBuild;

           
            
            transform.parent verwijst naar de scene zodat de bal in de scene beland en niet in je kannon */
            GameObject ball = Instantiate(prefab, transform.parent);

           
            ball.transform.rotation = transform.rotation;

           
            ball.GetComponent<Rigidbody2D>().AddForce(ball.transform.right * _launchForce, ForceMode2D.Impulse);

            
            ball.transform.position = transform.position;
        }
       
        if (_pressTimer < maximumHoldTime)
        {
            
            _pressTimer += Time.deltaTime;
        }
    }
}
## Opdracht 3.1 en 3.2

sinds mijn game niet precies het zelfde is als de opdracht, heb ik zelf een score en die stuff gedaan. Ik heb geen scores, ik heb gold in mijn game staan. Je moet de peggles hitten om de gold te kunnen krijgen. sommige peggles hebben meer waard, dus je moet de peggles die meer waarde heeft meerdere keren hitten.

## opdracht 4.1 en 4.2
ik heb ze beide gedaan


https://github.com/user-attachments/assets/ec93dab6-6188-4168-a87c-114d55e4ca5d


script:
using UnityEngine;
using TMPro;

public class GameManager : MonoBehaviour
{
    public static GameManager Instance;
    public int totalGold = 0;
    public TextMeshProUGUI goldText;

    private void Awake()
    {
        if (Instance == null)
            Instance = this;
        else
            Destroy(gameObject);
    }

    void Start()
    {
        UpdateGoldUI();
    }

    public void AddGold(int amount)
    {
        totalGold += amount;
        UpdateGoldUI();
    }

    void UpdateGoldUI()
    {
        if (goldText != null)
            goldText.text = "Gold: " + totalGold;
    }
}

ik heb deze script gesleept naar game manager en mn textmeshpro gesleept nr die script.


https://github.com/user-attachments/assets/47ede052-5031-445d-ac44-578dc1313684



Sinds ik een beetje slecht ben met coderen, ik heb een beetje hulp aan Ai gevraagd, want ik ben een beginner. Heb het gebruikt om ook beetje te leren. Als dat oke is.
