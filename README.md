# Tp Cryptosystème de Vignère

## Chiffrement de Vignère :
---
``` c++
//Fonction de chiffrement
string chiffrer(string plainText, string key)
{
    string cipherText = "";
   
    int alphabet[26] = {'A','B', 'C', 'D', 'E', 'F', 'G', 'H', 'I',
    'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U',
    'V', 'W', 'X', 'Y', 'Z'};

    //Tableau contenant les nombre correspondant aux lettres du texte clair
    int plainTextArray[plainText.size()];
   
    //Tableau contenant les nombres correspondant aux lettres de la clé
    int keyArray[key.size()];
   
    //Supprimer les espaces du texte clair
    for(int i=0; i<plainText.size(); i++)
    {
        if(isspace(plainText[i]))
            plainText.erase(i,1);
    }
   
    //Transformer le texte clair en majuscule
    for(int i=0; i<plainText.size(); i++)
    {
        plainText[i] = toupper(plainText[i]);
    }
   
    //Tableau de correspondance du texte clair
    for(int i=0; i<plainText.size(); i++)
    {
        plainTextArray[i] = plainText[i] - 'A';
    }
   
    //Transformer la clé en majuscule
    for(int i=0; i<key.size(); i++)
    {
        key[i] = toupper(key[i]);
    }
   
    //Tableau de correspondance de la clé
    for(int i=0; i<key.size(); i++)
    {
        keyArray[i] = key[i] - 'A';
    }
   
    //Tableau contenant le texte chiffré en nombres
    int cipherArray[plainText.size()];
   
    //Appliquer le chiffrement
    for(int i=0; i<plainText.size(); i++)
    {
        cipherArray[i] = (plainTextArray[i] + keyArray[i%key.size()])%26;
    }

    //Transformer les nombres en lettres
    for(int i=0; i<plainText.size(); i++)
    {
        cipherText += alphabet[cipherArray[i]];
    }
   
    return cipherText;
}



}

```
## Déchiffrement de Vignère :  

c'est le meme principe du chifferement mais à l'inverse
``` c++
string Dechiffrer(string plainText, string key)
{
    string dechif = "";
   
    int alphabet[26] = {'A','B', 'C', 'D', 'E', 'F', 'G', 'H', 'I',
    'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U',
    'V', 'W', 'X', 'Y', 'Z'};

    //Tableau contenant les nombre correspondant aux lettres du texte clair
    int plainTextArray[plainText.size()];
   
    //Tableau contenant les nombres correspondant aux lettres de la clé
    int keyArray[key.size()];
   
    //Supprimer les espaces du texte clair
    for(int i=0; i<plainText.size(); i++)
    {
        if(isspace(plainText[i]))
            plainText.erase(i,1);
    }
   
    //Transformer le texte clair en majuscule
    for(int i=0; i<plainText.size(); i++)
    {
        plainText[i] = toupper(plainText[i]);
    }
   
    //Tableau de correspondance du texte clair
    for(int i=0; i<plainText.size(); i++)
    {
        plainTextArray[i] = plainText[i] - 'A';
    }
   
    //Transformer la clé en majuscule
    for(int i=0; i<key.size(); i++)
    {
        key[i] = toupper(key[i]);
    }
   
    //Tableau de correspondance de la clé
    for(int i=0; i<key.size(); i++)
    {
        keyArray[i] = key[i] - 'A';
    }
   
    //Tableau contenant le texte chiffré en nombres
    int cipherArray[plainText.size()];
   
    //Appliquer le dechifferement
    for(int i=0; i<plainText.size(); i++)
    {
        cipherArray[i] =((plainTextArray[i]-keyArray[i%key.size()])%26+26)%26 ;
        
    }

    //Transformer les nombres en lettres
    for(int i=0; i<plainText.size(); i++)
    {
        dechif += alphabet[cipherArray[i]];
    }
   
    return dechif;
}
```
# Recherche exaustive 


##    trouver la clé de chiffrement de taille prédifinie   

> Avec la meme fonction déchiffer qu'on vient d'implémenter ou peut arriver à trouver une clé de taille 3 a l'aide des boucle for imbriqués  
```  c++
void findKey(string cipher)
{
    //La clé est de taille 3 K(i,j,k)
   
    for(int i=0; i<26; i++)
    {
        for(int j=0; j<26; j++)
        {
            for(int k=0; k<26; k++)
            {
                //Construire la clé
                int key[3] = {i, j, k};
               
                //Afficher le message clair
                Dechiffrer(cipher, key);
               
                //Afficher la clé correspondante
                cout << i <<" " << j << " " << k << endl;
            }
        }
    }
}
``` 
# Merci
