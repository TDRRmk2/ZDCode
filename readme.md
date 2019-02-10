# ZDCode 2.0
## The language that compiles to ye olde DECORATE!

Take this example:

```c
#UNDEFINE ANNOYING

class RunZombie inherits ZombieMan replaces ZombieMan #2055
{
    set Gravity to 0.4; // high up...
    set Speed to 0;
    is NOBLOCKMONST;
    set Speed to 0;
 
    label See
    {
        call SeeCheck;
        POSS AB 5 A_Recoil(-0.7);
        call SeeCheck;
        POSS AB 4 A_Recoil(-0.7);
        call SeeCheck;
        POSS ABCD 3 A_Recoil(-0.7);
        call SeeCheck;
        goto RunLoop;
    };

    function SeeCheck
    {
        TNT1 A 0 A_Chase;
        POSS A 0 A_FaceTarget();
    };

    function ZombieJump
    {
        if ( health > 5 )
            return;

        while ( z == floorz )
        {
            POSS A 5 [Bright];
            POSS A 11 ThrustThingZ(0, 30, 0, 1);
        };

        #ifndef ANNOYING
        while ( z > floorz )
        {
            POSS AB 4;
        };

        POSS G 9;
        POSS B 22;
        #endif
        
        POSS AB 2 A_Chase;
    };

    label RunLoop
    {
        x 2
        {
            POSS ABCD 2 A_Recoil(-0.7);
            call SeeCheck;
        };

        call ZombieJump;
        loop;
    };
}
```

This is what happens when that beauty goes through **ZDCode 2.0**:

```
Actor _Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_0 : Inventory {Inventory.MaxAmount 1}
Actor _Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_1 : Inventory {Inventory.MaxAmount 1}
Actor _Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_2 : Inventory {Inventory.MaxAmount 1}
Actor _Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_3 : Inventory {Inventory.MaxAmount 1}
Actor _Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_4 : Inventory {Inventory.MaxAmount 1}
Actor _Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_5 : Inventory {Inventory.MaxAmount 1}
Actor _Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_6 : Inventory {Inventory.MaxAmount 1}


Actor RunZombie : ZombieMan replaces ZombieMan 2055
{
    Gravity 0.4
    Speed 0
    Speed 0
    
    +NOBLOCKMONST
    
    States {
        F_SeeCheck:
            TNT1 A 0 A_Chase
            POSS A 0 A_FaceTarget
            TNT1 A 0 A_JumpIfInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_0", 1, "_CLabel0")
            TNT1 A 0 A_JumpIfInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_1", 1, "_CLabel1")
            TNT1 A 0 A_JumpIfInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_2", 1, "_CLabel2")
            TNT1 A 0 A_JumpIfInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_3", 1, "_CLabel3")
            TNT1 A 0 A_JumpIfInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_4", 1, "_CLabel4")
            TNT1 A 0 A_JumpIfInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_5", 1, "_CLabel5")
            TNT1 A -1
        
            F_ZombieJump:
            TNT1 A 0 A_JumpIf(!(health > 5), 2)
            TNT1 A 0 A_JumpIfInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_6", 1, "_CLabel6")
            Stop
            TNT1 A 0
        _WhileBlock0:
            TNT1 A 0 A_JumpIf(!(z == floorz), 3)
            POSS A 5  Bright
            POSS A 11 ThrustThingZ(0, 30, 0, 1)
            Goto _WhileBlock0
            TNT1 A 0
        _WhileBlock1:
            TNT1 A 0 A_JumpIf(!(z > floorz), 3)
            POSS A 4
            POSS B 4
            Goto _WhileBlock1
            TNT1 A 0
            POSS G 9
            POSS B 22
            POSS A 2 A_Chase
            POSS B 2 A_Chase
            TNT1 A 0 A_JumpIfInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_6", 1, "_CLabel6")
            TNT1 A -1
        
        See:
            TNT1 A 0 A_GiveInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_0")
            Goto F_SeeCheck
        _CLabel0:
            TNT1 A 0 A_TakeInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_0")
            POSS A 5 A_Recoil(-0.7)
            POSS B 5 A_Recoil(-0.7)
            TNT1 A 0 A_GiveInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_1")
            Goto F_SeeCheck
        _CLabel1:
            TNT1 A 0 A_TakeInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_1")
            POSS A 4 A_Recoil(-0.7)
            POSS B 4 A_Recoil(-0.7)
            TNT1 A 0 A_GiveInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_2")
            Goto F_SeeCheck
        _CLabel2:
            TNT1 A 0 A_TakeInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_2")
            POSS A 3 A_Recoil(-0.7)
            POSS B 3 A_Recoil(-0.7)
            POSS C 3 A_Recoil(-0.7)
            POSS D 3 A_Recoil(-0.7)
            TNT1 A 0 A_GiveInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_3")
            Goto F_SeeCheck
        _CLabel3:
            TNT1 A 0 A_TakeInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_3")
            goto RunLoop
        
        RunLoop:
            POSS A 2 A_Recoil(-0.7)
            POSS B 2 A_Recoil(-0.7)
            POSS C 2 A_Recoil(-0.7)
            POSS D 2 A_Recoil(-0.7)
            TNT1 A 0 A_GiveInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_4")
            Goto F_SeeCheck
        _CLabel4:
            TNT1 A 0 A_TakeInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_4")
            POSS A 2 A_Recoil(-0.7)
            POSS B 2 A_Recoil(-0.7)
            POSS C 2 A_Recoil(-0.7)
            POSS D 2 A_Recoil(-0.7)
            TNT1 A 0 A_GiveInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_5")
            Goto F_SeeCheck
        _CLabel5:
            TNT1 A 0 A_TakeInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_5")
            TNT1 A 0 A_GiveInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_6")
            Goto F_ZombieJump
        _CLabel6:
            TNT1 A 0 A_TakeInventory("_Call_NPaLK2i4Etrk1DERaszVFVbnG6JiT6KwJHX_6")
            Goto RunLoop
    }
}
```

Yes, I know; the compiled output looks ugly. But, hey, it's like expecting readability from a binary file!

Just slap the output in your WAD and... [look at what happens!](https://i.imgur.com/mr5wJ85.gifv)
