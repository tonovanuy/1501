public interface Project {
    void start();  // Почати проект
    void finish(); // Завершити проект
    String getDetails(); // Отримати інформацію про проект
}

public abstract class Employee {
    String name;

    public Employee(String name) {
        this.name = name;
    }

    public abstract void workOnProject(Project project);
}

public class Developer extends Employee {

    public Developer(String name) {
        super(name);
    }

    @Override
    public void workOnProject(Project project) {
        System.out.println(name + " працює над проектом: " + project.getDetails());
    }
}

public class Manager extends Employee {

    public Manager(String name) {
        super(name);
    }

    @Override
    public void workOnProject(Project project) {
        System.out.println(name + " контролює проект: " + project.getDetails());
    }
}

public class SoftwareProject implements Project {
    String name;

    public SoftwareProject(String name) {
        this.name = name;
    }

    @Override
    public void start() {
        System.out.println("Проект " + name + " почався!");
    }

    @Override
    public void finish() {
        System.out.println("Проект " + name + " завершено!");
    }

    @Override
    public String getDetails() {
        return "Програмний проект: " + name;
    }
}

public class ConstructionProject implements Project {
    String name;

    public ConstructionProject(String name) {
        this.name = name;
    }

    @Override
    public void start() {
        System.out.println("Будівництво проекту " + name + " розпочато!");
    }

    @Override
    public void finish() {
        System.out.println("Будівництво проекту " + name + " завершено!");
    }

    @Override
    public String getDetails() {
        return "Будівельний проект: " + name;
    }
}

public class Main {
    public static void main(String[] args) {
        // Створюємо співробітників
        Employee dev = new Developer("Артем");
        Employee manager = new Manager("Ірина");

        // Створюємо проекти
        Project software = new SoftwareProject("Розробка веб-сайту");
        Project construction = new ConstructionProject("Будівництво офісної будівлі");

        // Співробітники працюють над проектами
        dev.workOnProject(software);
        manager.workOnProject(construction);

        // Початок і завершення проектів
        software.start();
        software.finish();
        System.out.println(software.getDetails());

        construction.start();
        construction.finish();
        System.out.println(construction.getDetails());
    }
}

