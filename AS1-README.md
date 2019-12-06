
#Java

import java.util.ArrayList;
import java.util.Arrays;

public class Dog {

    private String name;
    private String breed;
    private String owner;

    private ArrayList <DogShowScore> showScores;


    public Dog (String name, String breed, String owner) {
        this.name = name;
        this.breed = breed;
        this.owner = owner;

        this.showScores = new ArrayList<> ();
    }

    public String getName () {
        return name;
    }

    public void setName (String name) {
        this.name = name;
    }

    public String getBreed () {
        return breed;
    }

    public void setBreed (String breed) {
        this.breed = breed;
    }

    public String getOwner () {
        return owner;
    }

    public void setOwner (String owner) {
        this.owner = owner;
    }

    public void addScore (DogShowScore newScore) {

        this.showScores.add (newScore);
    }

    public int getNumberOfEventsEntered () {
        return this.showScores.size ();
    }

    public double getShowScore () {

        final int scoreCount = this.showScores.size ();
        double score = 0;
        int[] scores = new int [scoreCount];

        if (scoreCount >= 3) {
            for (int i = 0; i < scoreCount; i++) {
                scores[i] = this.showScores.get (i).getScore ();
            }

            Arrays.sort (scores);

            score = (scores[scoreCount - 1] + scores[scoreCount - 2] + scores[scoreCount - 3]) / 3.0;
        }

        return score;

    }

    public int getBestScore () {

        int bestScore = 0;

        for (DogShowScore score: this.showScores) {
            if (score.getScore () > bestScore) {
                bestScore = score.getScore ();
            }
        }

        return bestScore;
    }

    public String getBestEvent () {

        int bestScore = this.getBestScore ();

        if (bestScore == 0) {
            return "";
        }
        else {
            for (DogShowScore score: this.showScores) {
                if (score.getScore () == bestScore) {
                    return score.getEvent ();
                }
            }
        }

        return "";

    }

    public String getOwnerDetailsAsString () {

        return this.getName () + " the dog is owned by " + this.getOwner () + ".";

    }
    public String getEventDetailsAsString () {

        return this.getName () + " the dog, got" + this.getShowScore () + "in the Jump Event";

    }

    public static void main(String[] args) {
        Dog theresa = new Dog ("Theresa", "pug", "Jeremy");
        Dog baxter = new Dog ("Baxter", "poodle","Tom");
        DogShowScore s1 = new DogShowScore("Jump",8);
        DogShowScore s2 = new DogShowScore("bestPawShake",9);
        DogShowScore s3 = new DogShowScore("waggiestTail",2);
        DogShowScore s4 = new DogShowScore("Jump",7);
        DogShowScore s5 = new DogShowScore("bestPawShake",10);
        DogShowScore s6 = new DogShowScore("waggiestTail",6);

        theresa.addScore(s1);
        theresa.addScore(s2);
        theresa.addScore(s3);
        baxter.addScore(s4);
        baxter.addScore(s5);
        baxter.addScore(s6);

        System.out.println(theresa.getOwnerDetailsAsString());
        System.out.println(theresa.getBestScore() + " was Theresa's best score");
        System.out.println(theresa.getShowScore() + " was Theresa's average score");
        System.out.println(baxter.getOwnerDetailsAsString());
        System.out.println(baxter.getBestScore() + " was Baxter's best score");
        System.out.println(baxter.getShowScore() + " was Baxter's average score");

    }

}
