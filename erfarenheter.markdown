---
layout: page
title: Erfarenheter
---

Jag har efter gymnasiet varit inblandad i en del programmerings projekt där jag har gjort programvara i form av bottar till spelet Tibia.
Jag började att programmera i <span style="color:blue">*vb6*</span> för att sen gå över till <span style="color:blue">*vb.net*</span>, där stannade jag ett par år för att sedan avsluta med <span style="color:blue">*c#*</span> med lite <span style="color:blue">*c++*</span>.
Jag har gjort mina program skriptbara nu senast använde jag mig utav en klass i .net som heter *CodeDom*.


Tack vara den kan det kan man få sin programvara skriptbar i antingen <span style="color:blue">*c#* </span> eller  <span style="color:blue">*vb.net*</span>.
Andra skript språk jag har provat på att implementera i mina program har varit <span style="color:blue">*vbscript*</span> och  <span style="color:blue">*lua*
</span>. 


Min erfarenhet av  <span style="color:blue">*vbscript*</span> var att det var enkelt att skriva men att supporten för <span style="color:blue">*vbscript*</span> var i princip helt dött.
Mina två stora program jag gjort ligger för närvarande på github, **MemoryScanner** och **Ladabot**.

Min ögonsten är **MemoryScanner** som är ett verktyg att hitta minnes addresses i Tibia, efter Tibia genomgått en uppdatering.
Tanken bakom är att strukturen i minnet inte förändras väsentligt, så med det kan man bara söka efter asm-code man känner till sen tidigare.

Strukturen för varje addressöking ärver strukturen ifrån en annan klass jag kallar GetAddress, men jag skriver i alla underklasser över strukturen med override. Fördelen med detta är att jag kan behandla alla object som en GetAddress klass men de egentligen är något annat.





```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Diagnostics;
namespace MemoryScanner.Addresses
{
    public class FullLight : GetAddresses
    {
        MemoryScanner memScan;
        MemoryReader memRead;
        AddressType Type;
        private int m_address;
        public FullLight(MemoryReader _memRead, MemoryScanner _memScan, AddressType _type)
        {
            this.memRead = _memRead;
            this.memScan = _memScan;
            this.Type = _type;
        }
        public override GetAddresses.AddressType AddressCategory
        {
            get
            {
                return Type;
            }
        }
        public override int Address
        {
            get
            {
                return m_address;
            }
            set
            {
                m_address = value;
            }
        }
        public override string Name
        {
            get
            {
                return "FullLight";
            }
        }
        public override void Search()
        {
             
            byte[] SearchBytes = new byte[] { 0x3D, 0xFF, 0x00, 0x00, 0x00, 0x0F, 0x4F, 0xC1, 0x53, 0x8B, 0x1D };
            List<int> values = memScan.ScanBytes(SearchBytes);
            if (values.Count > 0)
            {              
                m_address = values[0] + 9;
             
            }           
        }
        public override string GetString()
        {
            int val = 0;
            if (m_address == 0)
            {
                Search();
            }
            if (!Util.GlobalVars.ShowWithBase)
            {
                val = Address - memScan.BaseAddress;
            }
            else
            {
                val = Address;
            }
            return Name + " = 0x" + val.ToString("X");
        }
        public override bool CheckAddress()
        {
            return base.CheckAddress();
        }
    }
}
```