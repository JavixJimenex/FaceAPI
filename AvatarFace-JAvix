public class MonsterFace extends FaceGroup
{
  public MonsterFace(String id) {
    super(id);
    PShape s = createShape(ELLIPSE,40,0,200,200);
    s.setFill(color(255));
    s.setStroke(color(0)); 
    shape.addChild(s);
  }
}


public class MonsterEye extends AnimatedFeature
{
   public MonsterEye(String id, int x, int y) {
     super(id,x,y);
     open();
   }

   public PShape open() {
    shape = createShape(ELLIPSE,x,y,20,20);
    shape.setFill(color(0));
    shape.setStroke(color(0));
    return super.open();
  } 

  public PShape close() {
    shape = createShape(LINE,x-10,y+2,x+10,y+2);
    shape.setFill(color(0));
    shape.setStrokeWeight(4);
    shape.setStroke(color(250,0,0));
    return super.close();
  }  
}

public class MonsterEyeB extends AnimatedFeature
{
   public MonsterEyeB(String id, int x, int y) {
     super(id,x,y);
     open();
   }

   public PShape open() {
    shape = createShape(RECT,x,y,30,5);
    shape.setFill(color(0));
    shape.setStroke(color(0));
    return super.open();
  } 

  public PShape close() {
    shape = createShape(TRIANGLE,x-15,y+5,x+10,y+10,x-0,y-0);
    shape.setFill(color(100));
    shape.setStrokeWeight(2);
    shape.setStroke(color(150,0,0));
    return super.close();
  }  
}


public class MonsterMouth extends AnimatedFeature
{  
   public MonsterMouth(String id, int x, int y) {
     super(id,x,y);
     open();
   }
  
   public PShape open() {
    shape = createShape();
    shape.beginShape(TRIANGLE_STRIP);
    shape.fill(255);
    shape.stroke(0);
    shape.vertex(20, 75);
    shape.vertex(30, 20);
    shape.vertex(40, 75);
    shape.vertex(50, 20);
    shape.vertex(60, 75);
    shape.vertex(70, 20);
    shape.vertex(80, 75);
    shape.endShape(CLOSE);
    return super.open();
  } 

  public PShape close() {
    shape = createShape(LINE,x+25,y+50,x+75,y+50);
    shape.setFill(color(0));
    shape.setStrokeWeight(4);
    shape.setStroke(color(250,0,0));
    return super.close();
  } 
}


public class AvatarFace
{
    MonsterEye ojoIzq;
    MonsterEye ojoDer;
    MonsterEyeB cejaIzq;
    MonsterEyeB cejaDer;
  MonsterMouth boca;
   MonsterFace cara;
  
  public AvatarFace()
  {
    ojoIzq = new MonsterEye("ojoIzq",   0, 0);
    ojoDer = new MonsterEye("ojoDer", 100, 0);
    cejaIzq = new MonsterEyeB("cejaIzq",   -20, -20);
    cejaDer = new MonsterEyeB("cejaDer", 90, -20);
      boca = new MonsterMouth("boca",   0, 0);
      cara = new MonsterFace("puppet");  
    cara.add(ojoIzq);
    cara.add(ojoDer);
    cara.add(cejaIzq);
    cara.add(cejaDer);
    cara.add(boca);
    
  }

  public void draw(int x, int y) {
    cara.position(x,y);
    cara.draw();
  }

  public BasicState status(FeatureID id) {
    if (id == FeatureID.LeftEye) {
        return ojoIzq.status();
    } else if (id == FeatureID.LeftBrow ) {
        return cejaIzq.status();      
    }
    else if (id == FeatureID.RightEye) {
        return ojoDer.status();      
    }else if (id == FeatureID.RightBrow ) {
        return cejaDer.status();      
    }
    return BasicState.Undefined;
  }
   
  public void change(FeatureID id, Action action)
  {
    // PS BUG no-enum-switch 
    if (id == FeatureID.LeftEye) { // ojo izq?
      if (action == Action.closeEye) {
          cara.replaceShape(ojoIzq.getID(),ojoIzq.close());
      } else {
          cara.replaceShape(ojoIzq.getID(),ojoIzq.open());
      }
    } else if (id == FeatureID.RightEye) { // ojo der?
      if (action == Action.closeEye) {
          cara.replaceShape(ojoDer.getID(),ojoDer.close());
      } else {
          cara.replaceShape(ojoDer.getID(),ojoDer.open());
      } // if close
    } else if (id == FeatureID.Mouth) { // boca?
      if (action == Action.closeMouth) {
          cara.replaceShape(boca.getID(),boca.close());
      } else {
          cara.replaceShape(boca.getID(),boca.open());
      }
      // if close
    }
    else if (id == FeatureID.LeftBrow) { // cejaizq
      if (action == Action.closeEyeB) {
          cara.replaceShape(cejaIzq.getID(),cejaIzq.close());
      } else {
          cara.replaceShape(cejaIzq.getID(),cejaIzq.open());
      }
      // if close
    }
    else if (id == FeatureID.RightBrow) { // cejaDer
      if (action == Action.closeEyeB) {
          cara.replaceShape(cejaDer.getID(),cejaDer.close());
      } else {
          cara.replaceShape(cejaDer.getID(),cejaDer.open());
      }
      // if close
    }// else
  } // change()
} // AvatarFace class
