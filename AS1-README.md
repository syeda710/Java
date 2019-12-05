#JAVA
public class Dogs {

    private String name;
    private String breed;
    private String owner;
    private int score;

    public Dogs(String name, String breed, String owner, int score) {
        this.name = name;
        this.breed = breed;
        this.owner = owner;
        this.score = score;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getBreed() {
        return breed;
    }

    public void setBreed(String breed) {
        this.breed = breed;
    }

    public String getOwner() {
        return owner;
    }

    public void setOwner(String owner) {
        this.owner = owner;
    }
    public int getScore() {
        return score;
    }

    public void setScore(int score) {
        this.score = score;
    }
    public void increaseScore () {
        this.score ++;
    }
    @Override
    public String toString() {
        return "Dogs{" +
                "name='" + name + '\'' +
                ", breed='" + breed + '\'' +
                ", owner='" + owner + '\'' +
                ", score=" + score +
                '}';
    }

    public static void main(String[] args) {
        Dogs Theresa = new Dogs("Theresa", "pug","Batul", 7 );
        System.out.println (Theresa);
        Theresa.increaseScore();
        System.out.println(Theresa);
    }

    }
