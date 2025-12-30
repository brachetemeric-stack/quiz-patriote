# quiz-patriote
Teste tes connaissances sur l’histoire, les symboles et les valeurs de la France ! Ce quiz interactif te propose des questions variées, allant des événements historiques aux symboles nationaux. Que tu sois passionné d’histoire ou simplement curieux, découvre si tu es un vrai connaisseur du patrimoine français.
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Quiz pour mesurer votre attachement à la France en tant que patrie">
    <title>Quiz : Quel est ton niveau d'attachement à la France ?</title>
    <script crossorigin src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body>
    <div id="root"></div>
    
    <script type="text/babel">
        const { useState } = React;

        // Icône Flag
        const Flag = ({ className }) => (
            <svg className={className} fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M3 21v-4m0 0V5a2 2 0 012-2h6.5l1 1H21l-3 6 3 6h-8.5l-1-1H5a2 2 0 00-2 2zm9-13.5V9" />
            </svg>
        );

        // Icône Share2
        const Share2 = ({ className }) => (
            <svg className={className} fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M8.684 13.342C8.886 12.938 9 12.482 9 12c0-.482-.114-.938-.316-1.342m0 2.684a3 3 0 110-2.684m0 2.684l6.632 3.316m-6.632-6l6.632-3.316m0 0a3 3 0 105.367-2.684 3 3 0 00-5.367 2.684zm0 9.316a3 3 0 105.368 2.684 3 3 0 00-5.368-2.684z" />
            </svg>
        );

        // Icône Download
        const Download = ({ className }) => (
            <svg className={className} fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4" />
            </svg>
        );

        const Quiz = () => {
            const [currentQuestion, setCurrentQuestion] = useState(0);
            const [score, setScore] = useState(0);
            const [showResult, setShowResult] = useState(false);
            const [started, setStarted] = useState(false);

            const questions = [
                {
                    question: "Que ressens-tu quand tu penses aux racines et à l'histoire de la France ?",
                    answers: [
                        { text: "Peu de sentiment particulier", points: 0 },
                        { text: "Une profonde fierté et un lien personnel fort", points: 5 },
                        { text: "Une curiosité ou un intérêt modéré", points: 2 }
                    ]
                },
                {
                    question: "Reconnais-tu l'existence historique du peuple français et son héritage ?",
                    answers: [
                        { text: "Oui, je comprends et admet l'importance de son identité historique", points: 5 },
                        { text: "Non, je n'en suis pas conscient ou j'estime que ce n'est pas pertinent", points: 0 },
                        { text: "Partiellement, je connais certains aspects", points: 2 }
                    ]
                },
                {
                    question: "Que signifie pour toi \"être patriote\" ?",
                    answers: [
                        { text: "Aimer la France de manière générale", points: 2 },
                        { text: "Protéger et valoriser l'histoire, la culture et l'identité du peuple français", points: 5 },
                        { text: "Juste respecter la loi et les symboles officiels", points: 0 }
                    ]
                },
                {
                    question: "Si la France était menacée, comment réagirais-tu ?",
                    answers: [
                        { text: "Je défendrais activement le pays et son héritage", points: 5 },
                        { text: "Je ne m'impliquerais pas", points: 0 },
                        { text: "Je ferais ce que je peux selon la situation", points: 2 }
                    ]
                },
                {
                    question: "Comment perçois-tu l'idée que l'immigration importante pourrait transformer la composition historique de la population française ?",
                    answers: [
                        { text: "Cela peut modifier certains aspects, mais ce n'est pas fondamental", points: 2 },
                        { text: "Cela représente un enjeu pour préserver l'identité et l'héritage du peuple français", points: 5 },
                        { text: "Cela ne pose aucun problème, la France doit accueillir tous les peuples", points: 0 }
                    ]
                },
                {
                    question: "L'amour de la France selon toi, est-il suffisant pour être patriote ?",
                    answers: [
                        { text: "Je ne sais pas", points: 0 },
                        { text: "Non, il faut aussi connaître et préserver ses racines et son peuple", points: 5 },
                        { text: "Oui, aimer le pays suffit", points: 2 }
                    ]
                },
                {
                    question: "Comment percevrais-tu quelqu'un qui dit aimer la France mais ignore son histoire et ses racines ?",
                    answers: [
                        { text: "Cela peut être sincère, l'intention compte", points: 2 },
                        { text: "Peu important pour moi", points: 0 },
                        { text: "Son patriotisme me semble superficiel ou opportuniste", points: 5 }
                    ]
                },
                {
                    question: "Quel rôle joue la culture française dans ton attachement à la patrie ?",
                    answers: [
                        { text: "Elle renforce mon identité et mon lien avec la France", points: 5 },
                        { text: "Peu ou pas d'importance", points: 0 },
                        { text: "Elle est secondaire, ce qui compte c'est le territoire", points: 2 }
                    ]
                },
                {
                    question: "Te considères-tu responsable de transmettre et protéger l'identité française aux générations futures ?",
                    answers: [
                        { text: "Moyennement, je fais ce que je peux", points: 2 },
                        { text: "Oui, c'est essentiel", points: 5 },
                        { text: "Non, ce n'est pas ma responsabilité", points: 0 }
                    ]
                },
                {
                    question: "L'attachement à ta patrie t'empêche-t-il de respecter les autres cultures et peuples ?",
                    answers: [
                        { text: "Non, on peut être fier de sa patrie sans rejeter les autres", points: 5 },
                        { text: "Parfois, cela peut créer des tensions", points: 2 },
                        { text: "Oui, je privilégie toujours ma propre culture", points: 0 }
                    ]
                }
            ];

            const handleAnswer = (points) => {
                const newScore = score + points;
                setScore(newScore);

                if (currentQuestion + 1 < questions.length) {
                    setCurrentQuestion(currentQuestion + 1);
                } else {
                    setShowResult(true);
                }
            };

            const getResult = () => {
                const percentage = (score / 50) * 100;
                
                if (percentage <= 30) {
                    return {
                        title: "Peu conscient de son identité et de ses racines",
                        message: "Votre attachement à la France en tant que patrie semble limité. Vous pourriez explorer davantage l'histoire et l'héritage culturel français pour approfondir votre lien avec votre pays.",
                        color: "text-red-600"
                    };
                } else if (percentage <= 60) {
                    return {
                        title: "Conscience moyenne, attachement modéré",
                        message: "Vous avez une conscience modérée de votre identité et de vos racines françaises. Vous appréciez certains aspects de l'héritage français tout en gardant une approche équilibrée.",
                        color: "text-orange-600"
                    };
                } else {
                    return {
                        title: "Fortement attaché à sa patrie et conscient de ses racines",
                        message: "Vous démontrez un fort attachement à la France et une profonde conscience de ses racines historiques et culturelles. Vous valorisez l'identité et l'héritage du peuple français.",
                        color: "text-green-600"
                    };
                }
            };

            const resetQuiz = () => {
                setCurrentQuestion(0);
                setScore(0);
                setShowResult(false);
                setStarted(false);
            };

            const shareScore = () => {
                const percentage = Math.round((score / 50) * 100);
                const result = getResult();
                const shareText = `J'ai fait le quiz "Quel est ton niveau d'attachement à la France ?" et j'ai obtenu ${percentage}% !\n\nRésultat : ${result.title}\n\nFais le quiz toi aussi !`;
                
                if (navigator.share) {
                    navigator.share({
                        title: 'Quiz : Attachement à la France',
                        text: shareText,
                    }).catch(() => {
                        copyToClipboard(shareText);
                    });
                } else {
                    copyToClipboard(shareText);
                }
            };

            const copyToClipboard = (text) => {
                navigator.clipboard.writeText(text).then(() => {
                    alert('Score copié dans le presse-papiers !');
                }).catch(() => {
                    alert('Impossible de copier le score');
                });
            };

            const downloadScoreImage = () => {
          
