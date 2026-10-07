# Furniture Alignment Correction for NPC´s (No esp) 4.0.0

Source: https://www.loverslab.com/files/file/13259-furniture-alignment-correction-for-npc%C2%B4s-no-esp/

## About This File

This is a very small script which can be attached to furnitures, to correct the position of NPC´s entering said furnitures.

If you have ever used something from Zap, you should know the problem.

This mod adds the script `pamaFurnitureAlignmentHelper`.

Attach it to any furniture added by a mod, and the problem should be gone.

Install with mod manager of your choice or drop manually into data folder (or your own mod folder if you want to make new furnitures yourself).

The properties can safely be ignored. Only use them for Furnitures which have an Offset to their entry points.

The vast majority of Furnitures don't have one. If they do, you can find the values for them with NifSkope in their respective `.nif` files.

## Full Source Code

```papyrus
Scriptname pamaFurnitureAlignmentHelper extends ObjectReference
{Created by Pamatronic - Can Be attached To furnitures to correct FNIS misalignment}

float property EntryPointOffset_X Auto
float property EntryPointOffset_Y Auto
float property EntryPointOffset_Rotation Auto

Actor Victim
int maxIterator

Event OnActivate(ObjectReference akActionRef)
    if ((akActionRef as actor).getSitState()!=4) || akActionRef != game.getPlayer()
        Victim=akActionref as Actor
        maxIterator=0
        RegisterForSingleUpdate(0.1)
    endIf
EndEvent

Event OnUpdate()
    if (Victim.getPositionX()!=translateLocal(EntryPointOffset_X, EntryPointOffset_Y, true) || Victim.getPositionY()!=translateLocal(EntryPointOffset_X, EntryPointOffset_Y, false)) && victim.getSitstate()==3 && maxIterator <=15
        Victim.translateTo(
            translateLocal(EntryPointOffset_X, EntryPointOffset_Y, true),
            translateLocal(EntryPointOffset_X, EntryPointOffset_Y, false),
            Z,
            self.getAngleX(),
            self.getAngleY(),
            self.getAngleZ()+EntryPointOffset_Rotation,
            50.0,
            0.0
        )
        maxIterator+=1
        RegisterForSingleUpdate(0.5)
    else
        victim=none
    endIf
EndEvent

float Function translateLocal(float OffsetX, float OffsetY, bool XorY)
    ;XorY=true >> calculate x offset / XorY=true >> calculate y offset
    float tmpRotation =self.getAngleZ()+(90.0)

    if XorY
        return X+(math.sin(tmpRotation)*OffsetX)+ (math.cos(tmpRotation)*OffsetY)
    else
        return Y+(math.sin(tmpRotation)*-(OffsetY))+ (math.cos(tmpRotation)*OffsetX)
    EndIf
EndFunction
```

## Notes NEFARAM-Rhiven

- Ce mod ne contient **pas d'ESP** et n'ajoute pas de gameplay autonome.
- Il fournit uniquement le script `pamaFurnitureAlignmentHelper`, destiné à être attaché à des furnitures qui présentent un mauvais alignement.
- À conserver comme **outil technique optionnel**, utile seulement si un furniture PAMA / ZaZ précis montre un défaut d'alignement.
- Inutile de l'installer systématiquement si aucun furniture du build n'en dépend explicitement.
- Le code utilise `TranslateTo` pour repositionner l'acteur vers le point d'entrée local du furniture, avec offsets X/Y/rotation optionnels.
- À ranger dans les modules **optionnels / support technique** du chantier PAMA.
